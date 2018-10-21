---
@title[Start]
@snap[east]
@size[2em](社内鯖管のための<br>ツールなお話)
<br><br>
@size[1em](鍛治 拓人)  
@size[0.5em](株式会社スカイアーチネットワークス)  
@size[0.5em](技術本部 開発部)
@snapend

---?opacity=50

### Whois

```Bash
名前
    鍛治 拓人
所属
    株式会社スカイアーチネットワークス　技術本部 開発部
生まれ
    奈良県
経歴
    独立系中小SIer企業(1.5年)→スカイアーチ(1.2年)
    ほぼ開発側
        社内ツールの保守・運用
        Ansible
        CloudFormation
        Jenkins
        Lambda
        PHP、Python、Java
```
Note:
名前、東京にあるスカイアーチ
けど、生まれは奈良で大学も近大

PHPのバージョンアップの作業とかでリプレース作業
最近はサーバレスとしてLambdaを
DevOpsの区切りなら、Dev側

---

### 社内ツール
* 社内の総合的な情報を扱う社内システム
    * 運用で使う情報
    * 顧客情報
* バックアップシステム
    * Lambdaを使ったサーバレス
    * AMI

Note:
主に私がかかわったのがこの2つ
今回はバックアップシステムについて

---

### 旧バックアップシステム
* バックアップシステム（既存）
    * EC2インスタンス上
    * Rails
    * 対象：EBSスナップショット
    
Note:

---

### 新バックアップシステム
* バックアップシステム（サーバレス）
    * Lambda
    * Python
    * 対象：AMI

* 監視避けたい
* SLAも一応出たよ
https://aws.amazon.com/jp/lambda/sla/

Note:
コストの削減やWindowsのライセンス問題、お客様からの要望等々、
サーバレスに移行の流れから、既存システムを移行していた

---
#### ところでバックアップといえば・・・
* Amazon Data Lifecycle Manager(DLM)
    * 東京リージョンが2018/8/16 に追加  
    [Amazon データライフサイクルマネージャーのリージョンでの拡充](https://aws.amazon.com/jp/about-aws/whats-new/2018/08/amazon-data-lifecycle-manager-regional-expansion/)
    * EBSスナップショット
    * 世代管理

* 要件を満たすのならDLMも

---

### サーバレスの恩恵(私見)
* プログラマがサービスを提供できる
    * 運用や監視が楽になる
    * サービスに集中できる
    * 構成で必要なものがあっても、コードでできる

Note:
主語を大きくしすぎると炎上する（笑）

一つサービスを作るにしても、サーバがないと・・・

サーバの構築を楽に、コードで・・・
開発と本番環境の差でエラーが・・・
    コンテナがあったけども
docker-compose.ymlすらいらなくなる
Devに忌避感を感じる？

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
var="test"

echo ${var}
```
@snapend

* コードを書くという点では同じ

@ulend

Note:
｜　パイプ
カレントディレクトリ以下の全ファイルからxxxという文字列を検索

---
### AnsibleやChef
* ShellからよりDevより

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

---
### 気軽にコードを書いてみる
- 

Note:

+++
### まとめ
- サーバレスバックアップシステム
- 開発者でもサービスが簡単に
- 案外、コードを書くのは身近

Note:
毛嫌いだけはしないでほしい
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


IoTデバイスの相互作用でブロックチェーンでふるまいを変える
背景
    なんおために？
    どんな技術で？

イーサリアム



@snap[south fragment]
てｓｔ
@snapend