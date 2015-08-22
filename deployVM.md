クラウド上に環境を設定する(railsセットのみ)
===
[chiemi627/vagrant_cookbook_centos70](https://github.com/chiemi627/vagrant_cookbook_centos70)
を使ってクラウド上に環境を設定することができます。ここではIDCFクラウド（cloudstack）を想定した環境構築の
方法について書きます。

作業手順
---
* 設定ファイルを取得
```bash
 % git clone https://github.com/chiemi627/vagrant_cookbook_centos70.git
 % cd vagrant_cookbook_centos70
```
* .envファイルを作り、リモート環境の設定を記入する
```bash
 % cp dot.env.sample .env
```
* .envファイルに記入が必要な情報は以下の5つです
	* API Key
	* Secret Key
	* Key Pair
	* IP Address
	* Private Key Path
これらの情報の取得方法に関しては http://www.idcf.jp/blog/cloud/api_autoscale2/ を参考にしてください。
* リモート環境にGuestOSを構築する
```bash
 % vagrant up --provider=cloudstack
```
完了するまでには数十分かかります。
途中で、
* 途中で以下のメッセージが表示されて止まってしまった場合には下記の対応をしてください。
```
==> default: sudo を実行するには tty がなければいけません。すみません
```

```bash
% vagrant ssh
vagrant@guestos> sudo visudo
```
viエディタで設定ファイルが開くので

```
 Defaults: requiretty
```
となっているところを

```
 Defaults: !requiretty
```
に変更して保存してログアウト。そのあと以下を実行してください。

```bash
% vagrant provision
```

* 完了したらsshでログインして動作確認をしてみてください
```bash
 % vagrant ssh
```
* Boxファイルを作る
```bash
 % vagrant package
```
カレントディレクトリにpackage.boxが作られます。

* Boxファイルを他の開発者と共有する
  * https://atlas.hashicorp.com/ にアカウントを作ってここに置くのが手っ取り早いです







 
