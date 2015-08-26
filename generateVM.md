開発環境を構築する
===
ここではRailアプリを開発する基本的な環境が整った仮想マシンファイルを
ダウンロードして自分のPCの上にインストールする方法について説明します。

* 環境構築の準備がお済みでない方は [準備](preparation.md)へ。

作業手順
---
* 環境設定ファイルを置くためのディレクトリを作成する
```bash
 % mkdir enpit
 % cd enpit
```
* 準備
 * Railsセットの場合
 ```bash
  % vagrant init chiemi627/centos7.0-rails
 ```
 * CakePHPセットの場合
 ```bash
  % vagrant init chiemi627/centos7.0-cakephp-mysql
 ```

* 環境構築
```bash
 % vagrant up --provider virtualbox
```

実行が完了したら終了です。

* 問題が起きた時
 * mountができないと言われて落ちたら→以下のコマンドを実行してみてください
 ```bash
 % vagrant ssh
 (guest osにログインするので,以下のコマンドを実行)
 > sudo /etc/init.d/vboxadd setup
 > exit
 (host osに戻るので)
 % vagrant reload
 ```
 * ネットワーク環境が貧弱でvagrant cloudからの仮想マシンダウンロードがしんどかったら
 * 渡辺が直接ファイル（package.box）をお渡ししますので以下のコマンドを実行してください
 ```bash
 (package.boxを作業ディレクトリ下に置く)
 % vagrant box add centos_cake package.box
 % vagrant init centos_cake
 % vagrant up
 ```

* 実行後の状態
 * Railsセットの場合
   * [Railsセットハンズオン資料 by 産技大enpit](https://goo.gl/9ddYIs)の第１章の途中、「enPiT仮想化環境にログイン」から進められる状態
 * CakePHPセットの場合
   * /var/www/htmlの下にcakephp3をインストールしてある
   * http://localhost:8080 でページが見えるはず
   * CakePHPの場合はハンズオン資料はありません


開発環境の利用方法
---
### ログイン
```bash
 % vagrant ssh
```
で仮想マシンへログインできます。 

### ホストOSのファイルをゲストOSの方に置く
vagrant upを実行したディレクトリはゲストOSの/vagrant フォルダにマウントされています。

### 仮想マシンをシャットダウンする
```bash
 % vagrant halt
```

### sshでログインしたい
```bash
 % vagrant ssh-config
```
で出力される内容を ~/.ssh/config 上にコピーすればsshでおなじようにログインできます。
例えば

```.ssh/config
Host enpit
  HostName 127.0.0.1
  User vagrant
  Port 2222
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile /Users/chiemi/enpit/.vagrant/machines/default/virtualbox/private_key
  IdentitiesOnly yes
  LogLevel FATAL
```

とし、
```bash
% ssh enpit
```
とするとvagrant sshと同じ設定でログインできます。

