開発環境の構成を変更する
===
[開発環境(仮想マシン)を構築する](generateVM.md) で用意された仮想マシンを作成するための
設定ファイルは [chiemi627/vagrant_cookbook_centos70](https://github.com/chiemi627/vagrant_cookbook_centos70)にあります。これをダウンロードして自分のBoxファイルを作って共有することができます。

作業手順
---
* 設定ファイルを取得
```bash
 % git clone https://github.com/chiemi627/vagrant_cookbook_centos70.git
 % cd vagrant_cookbook_centos70
```
 
* Berksfile, Vagrantファイルを書き換える
  * 具体的な書き換え方は割愛します。
  * それぞれ VagrantやChef-soloを勉強して試してみてください
  * 最初は書き換えずに次の手順に進んだ方がエラー時に問題が切り分けられて良いかも。
  
* ローカル環境にGuestOSを構築する
```bash
 % vagrant up --provider=virtualbox
```
完了するまでには数十分かかります。

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







 
