事前準備
===
パッケージ管理システムの導入
---
インストール作業すをするのにパッケージ管理システムを導入します。
MacOSではhomebrewやMacPorts, Linuxではyumやapt-getなどがあります。
それぞれの環境に適したものをお使いください。

ここではWindowsのパッケージ管理システムChocolateyを紹介します。

### for Windows (Chocolatey)
1. コマンドプロンプトを右クリックして「管理者として実行」を選択
2. ChocolateyのWebページを開き、トップページにあるスクリプトをコピーペーストして実行
```
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
```
実行が終わったらインストール完了

* スクリーンキャスト
 (産技大の中鉢先生が作成したものをお借りしてます。以下同様）
  * http://youtu.be/ZBtKgq9seKo

Git, VirtualBoxとVagrantのインストール
---
パッケージ管理システムを使ってGit, VirtualBoxとVagrantをインストールしてください。
詳細はスクリーンキャストで。
* chocolateyの場合
```
% choco install git virtualbox vagrant
```
* スクリーンキャスト
* http://youtu.be/MQHDRIUP3hI

Vagrantプラグインのインストール
---
ホストOSとゲストOS間の操作を便利にするプラグイン(Guest Addition)を最新化
するプラグインをインストールします。

```bash
 % vagrant plugin install vagrant-vbguest
```

Git bashの設定（for Windows)
---
Git bashを起動してフォントや作業フォルダの設定をします。
詳細はスクリーンキャストを参照。

* スクリーンキャスト
  * http://youtu.be/eNlQpInE3Xg


これで準備は終了です。
