@title[社内鯖管のためのツールなお話]

@snap[east]
@size[2em](社内鯖管のための<br>ツールなお話)
<br><br>
@size[1em](鍛治 拓人)  
@size[0.6em](株式会社スカイアーチネットワークス)  
@size[0.6em](技術本部 開発部)  
@size[0.4em](2018/10/24)
@snapend

Note:
Press "S"

---?opacity=50

### Whois

```Bash
名前
    鍛治 拓人
所属
    株式会社スカイアーチネットワークス　技術本部 開発部
生まれ
    東大阪　育ち：奈良
経歴
    独立系中小SIer企業(1.5年)→スカイアーチ(1.2年)
    ほぼ開発側
        社内ツールのサポート、機能追加
        Ansible
        CloudFormation
        Jenkins
        Lambda
        PHP、Python、Java
```
Note:
名前、東京にあるスカイアーチ
けど、生まれは奈良

最初は開発会社で1年前にスカイアーチにJoin
そのため、基本的に開発のタスクを
PHPのバージョンアップでリプレース作業
AnsibleやCfn、Jenkins
最近はLambdaでサービスを
DevOpsの区切りなら、Dev側

いい機会だったので、社内でLTがあったら話したいことを書いてみた

---

### 社内ツール
* 社内の総合的な情報を扱う社内システム
    * 運用で使う情報
    * 顧客情報
* バックアップシステム（←こっち）
    * Lambdaを使ったサーバレス
    * AMI

Note:
主に私がかかわったのがこの2つ
今回はバックアップシステムについて思ったこと

---

### 旧バックアップシステム
* バックアップシステム（既存）
    * EC2インスタンス上
    * Rails
    * 対象：EBSスナップショット

* コスト削減
* Windows、RHELのライセンス
* お客様からの要望

Note:
コストの削減やWindows、RHELのライセンス問題、お客様からの要望から
サーバレスに移行の流れから、既存システムを移行していた

---

### 新バックアップシステム
* バックアップシステム（サーバレス）
    * Lambda
    * Python
    * 対象：AMI

* 最近、SLAも
https://aws.amazon.com/jp/lambda/sla/

Note:


---
#### ところでバックアップといえば・・・
* Amazon Data Lifecycle Manager(DLM)
    * 東京リージョンが2018/8/16 に追加  
    [Amazon データライフサイクルマネージャーのリージョンでの拡充](https://aws.amazon.com/jp/about-aws/whats-new/2018/08/amazon-data-lifecycle-manager-regional-expansion/)
    * EBSスナップショット
    * 世代管理

* 要件を満たすのならDLMも

Note:

---

### サーバレスの恩恵(私見)
* プログラマがサービスを提供できる
    * 運用や監視が楽になる
    * サービスに集中できる
    * 構成で必要なものがあっても、コードでできる

Note:
Devの人間からサーバレスを見たとき
主語を大きくしすぎると炎上する（笑）

一つサービスを作るにしても、サーバが必要だったり、
障壁があった
構築を楽にするためにIaCやコンテナがあったけども
サーバレスで一気に楽に
Devにとっては近づいたが、Opsからはどうなんだろう、と

---

### プログラミングを遠く感じる？
@ul

@snap[fragment]
* ワンライナーのコマンド

```Bash
find ./ -name '*'|xargs grep 'xxx'
```
@snapend

@snap[fragment]
* Shellスクリプト

```Bash
var="Hello World"

echo ${var}
```
@snapend

* コードを書くという点では同じ

@ulend

Note:
｜　パイプ
まず、プログラム自体を遠く感じる？
でも、近いことをやってるはず
プログラムではなく、コードとしてみる

カレントディレクトリ以下の全ファイルからxxxという文字列を検索

---
### もっとDevよりに
* IaC(AnsibleやChef)

~~~python
{% for hostname in hostnames %} 
<VirtualHost *:80> 
  ServerName {{ hostname.hostname }}
  ...
{% endfor %}
~~~

~~~yaml
hostnames:
  - hostname: hostname1.com
  - hostname: hostname2.com
~~~

出力
~~~Bash
<virtualhost *:80>
  ServerName hostname1.com
  ...
<virtualhost *:80>
  ServerName hostname2.com
~~~

Note:
ShellスクリプトよりDevより
Ansibleで考えると、
テンプレートファイル、Jinja2

---
### 気軽にコードを書いてみる
- 何回も書いたことが・・・
- 面倒な手順が・・・

@snap[fragment]
コードをアイテムや武器
@snapend

Note:
これまでに何回も書いたことがあるな、
今の作業をもっと楽にしてくれるもの、自分の武器とかアイテムとして考える
PGを書くことにフォーカスではなく、自分が楽できるために使うもの

プログラムを書いて楽にするではなく、
楽をしたいから、プログラムを書く。と考える

きっと、Ops側からだからこそ作れるコード、プログラムが

+++
### まとめ
- サーバレスバックアップシステム
- 開発者でもサービスが簡単に
- 案外、コードを書くのは身近

Note:  
Devの人間がIaCやサーバレスのバックアップシステムの作成を通して
逆順でIaC→プログラムが少しでも近いものと認識が変わってくれたら
サーバレスに挑戦してDevの人間では考えられなかった、アーキテクトで驚きを起こしてください、

↓で表示
---
@snap[east]
@size[1.7em](もっとコードを書きませんか？)
@snapend
---
@title[ありがとうございました]
@snap[midpoint]
<h4>ご清聴ありがとうございました</h4>
@snapend

---
---
--- 
## とりあえず
* 伝えたいこと
    * 主題
    * 副題
    * 何を
* 問題
    * 原因
* 提案
    * 解決策
    * 効果
    * 今後
---
## Page 3
![alt](assets/image_name.png)
---