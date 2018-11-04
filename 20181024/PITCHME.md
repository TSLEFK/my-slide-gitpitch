---

### 関わった社内ツール
* 社内の総合的な情報を扱う社内システム
    * 運用で使う情報
    * 顧客情報
* バックアップシステム（←こっち）
    * Lambdaを使ったサーバレス
    * AMI

Note:
- 主に私がかかわったのがこの2つ
- バックアップシステムの開発で思ったこと

---

### 旧バックアップシステム
* バックアップシステム（既存）
    * EC2インスタンス上
    * Ruby on Rails
    * 対象：スナップショット

* 要望
    * コスト削減
    * Windows、RHELのライセンス
    * お客様から

Note:
- コストの削減やライセンス問題、お客様からの要望と
- サーバレスに移行の流れから... 

---

### 新バックアップシステム
* バックアップシステム（サーバレス）
    * Lambda
    * Python
    * 対象：AMI
        * 最近(10/9)、SLAも  
        [AWS Lambda Service Level Agreement](https://aws.amazon.com/jp/lambda/sla/)

Note:
要望や問題の解決

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
* Devにとっては色々と問題が
    * サーバの用意
    * 環境で設定が異なる
    * 監視

Note:
主語を大きくしすぎると炎上しやすい

Devの人間からサーバレスを見たとき
一人で一つサービスを作るにしても、いろいろな問題があった
それが・・・

---

### サーバレスの恩恵(私見)
* プログラマがサービスを提供できる
    * 運用や監視が楽になる
    * サービスに集中できる
    * 構成で必要なものがあっても、コードでできる

@snap[south fragment]
Opsにとっては？
@snapend

Note:
ある程度サーバレスで楽に。
ところでサーバレスはDevにとってはいいが、Opsにとっては？
まず、サーバレス以前にOpsにとってプログラムって遠く思われてるのかな？
社内的に嫌厭されてる感がいなめない、勝手ながらそう思った
---

### プログラミングを遠く感じる？

@ul

@snap[fragment]
* コマンド

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
- でも、近いことをやってるはず
- コマンドやShellスクリプト

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

@[1](Pythonと同じ)

Note:
更にShellスクリプトよりもDevよりIaC
Ansibleで考えると、
テンプレートファイルで使うJinja2でVirtualHostを書く回数を減らす
For文を使っている
これはもう、Python

---
### 気軽にコードを書いてみる
- 何回も書いたことが・・・
- 面倒な手順が・・・

@snap[west fragment]
もっと楽にするもの
@snapend

@snap[fragment]
@snap[midpoint]
＝ 
@snapend

@snap[east]
アイテムや武器
@snapend
@snapend

@snap[south fragment]
~~プログラムを書く~~  
楽するための手段
@snapend

Note:
- 何回も書いたことがあるな、面倒だな、を
- 今の作業をもっと楽にしてくれるもの
- 自分の武器とかアイテムとして考える
- プログラミングではなく、自分が楽するためのいつの手段

- プログラムを書いて楽にするではなく、
楽をするための手段のひとつ。と考える

- どう楽にするかで、Devではみえなかったアーキテクチャや視点をOpsだからできることがある
- サーバレスに踏み出す一歩として、・・・

---
@title[最後に]

@snap[midpoint]
@size[1.3em](もっと~~コードを書き~~<br>楽をしませんか？)
@snapend

Note:
少しでもサーバレスに興味を持っていただければ、としてLT終わります
---

@title[締め]
@snap[midpoint]
@size[0.8em](ご清聴ありがとうございました)
@snapend

---
+++
@title[まとめ]
### まとめ
- サーバレスバックアップシステム
- 開発者でもサービスが簡単に
- 案外、コードを書くのは身近

Note:  
Devの人間がIaCやサーバレスのバックアップシステムの作成を通して
逆順でIaC→プログラムが少しでも近いものと認識が変わってくれたら
サーバレスに挑戦してDevの人間では考えられなかった、アーキテクトで驚きを起こしてください、
時間があれば、↓で表示
