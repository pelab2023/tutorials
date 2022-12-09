# tutorials

HP作成のチュートリアル。各項目の詳細な資料は、要望があれば作ります。</br>
この資料はpublicに設定されているため、**パスワード等は書き込まないでください**。</br>
基本的には、新b3のHP係を中心に活動することになります。

## 開発環境について

### テキストエディタ

各種コーディングに必要。</br>
VSCodeが使いやすくておすすめですが、使い慣れたものがあればそちらを使いましょう。

### Linux環境について

Windowsの人は、Linux環境を入れると便利です（と先輩に教わりましたが、私は使ってません）。</br>
プログラミング基礎/応用やシミュレーション演習(必修)でも必要になるため、まだない人はこの機会に導入してもいいかもしれません。

linux環境としては、
- WSL(Windows subsystem for Linux) : Windows上でLinuxを動かせる機能。こっちがおすすめ。</br>
  WSL1(旧版)とWSL2(新版)があります。違いは[公式ページ](https://docs.microsoft.com/ja-jp/windows/wsl/compare-versions)に書いてあります。</br>
  OSはUbuntuがおすすめ。Microsoft Storeから入れられます。
  - WSL1 : 旧版。初期設定ではこちら。Windows側へのファイルアクセスが速め。後からでも移行できるので、とりあえずこちらを使うのがおすすめ。
  - WSL2 : 新版。完全な仮想環境で、設定がやや面倒。仮想環境内のファイルへのアクセスが高速。
- Cygwin : なぜかプログラミング基礎などで推奨される。多分WSLを使える先生/TAがいないだけなので、WSLが推奨。</br>
  既に導入している場合は、こちらでもいいです。

Macの人はMacのターミナルでほぼ同じコマンドが使えます。

### git

Linux環境では初めから入っています。</br>
私はWindowsのコマンドプロンプトから操作しているので、同じようにしたい場合は[こちらのページ](https://aprico-media.com/posts/8554)を参考にしてください。</br>
Macではターミナルから、
```bash
brew install git
```
でインストールできます。

## webページの実装について

- トップページ、各企画ページなどを2020年のコードと2022年のデザインをベースに作成します。
- デザインはパソコン(pc)用とスマホ(sp)用の両方に対応させます。
- 紹介文や写真は各企画のリーダーなどに考えてもらってください。

### 参考：過去のページ

#### 2020年まで

HPは生html/css/jsだけで書かれていて、新b3のHP担当2、3人が担当していました。
- [2016年度](https://www.pemayfes.t.u-tokyo.ac.jp/2016)
- [2017年度](https://www.pemayfes.t.u-tokyo.ac.jp/2017)
- [2018年度](https://www.pemayfes.t.u-tokyo.ac.jp/2018)
- [2019年度](https://www.pemayfes.t.u-tokyo.ac.jp/2019)
- [2020年度](https://www.pemayfes.t.u-tokyo.ac.jp/2020)

#### 2021, 2022年

オンライン対応、スマホ対応でUIを充実させるため、Next.jsというフレームワークを使いました。</br>
コードは複雑化していますが、基本構成は2020年までと変わりません。</br>
注意として、コンパイルによりHTML/CSS/JSのコードを生成する仕様上、ブラウザに送られてくるソースはとても読めたものではないです。

コードを見たい場合は、サーバ上にあるものを見てください。

- [2021年度](https://www.pemayfes.t.u-tokyo.ac.jp/2021)
- [2022年度](https://www.pemayfes.t.u-tokyo.ac.jp/2022)

## 勉強してほしいこと

"*" 付きは必須事項。

### git*

まずそもそも、共同開発ができるようなバージョン管理ツールがないと開発ができません。去年はgitを使いました。

### HTML/CSS/JavaScript/PHP*

フロントエンド(=ブラウザ側)アプリケーション開発の基本。</br>
極論、HTML/CSSだけでもウェブサイトは作れる...が、UIを作るにはJavaScriptが必要で、さらにPHPを使うといろいろ便利。

拡張子は、
- HTML：.html（今回この拡張子は使わない）
- CSS：.css
- JavaScript：.js
- PHP：.php

学ぶ手段は何でもいいですが、個人的には[Progate](https://prog-8.com/)がおすすめです。

#### 参考資料

- https://developer.mozilla.org/ja/docs/Learn/Front-end_web_developer

## サーバ管理について

webparkという東大で借りている共有サーバを使います。</br>
実体は[さくらのレンタルサーバ](https://rs.sakura.ad.jp/)で、[コントロールパネル](https://secure.sakura.ad.jp/rs/cp/)内のファイルマネージャから操作できます。</br>
ドメイン名とパスワードは別途共有します。

### ディレクトリ構成

WindowsやMacにおけるフォルダのことを、サーバのOS(などのLinux系OS)ではディレクトリと呼びます。</br>
各ファイルの内容はファイル先頭に書いてあります。

www : 公開されるディレクトリ。これ以外のディレクトリは基本いじらない。(*1)<br/>
├── .htaccess : Webサーバの設定ファイル。<br/>
├── .htpasswd : Basic認証のパスワード設定用ファイル。<br/>
├── index.html->20xx/.../index.html : メインページの実体へのリンク。(*2)<br/>
├── 201x : 201x年度のディレクトリ。<br/>
├── 2020 : 2020年度のディレクトリ。<br/>
├── 2021 : 2021年度のディレクトリ。パソコン版(/pc)とスマホ版(/sp)に分かれています。<br/>
　　├── pc : PC版。<br/>
　　　　├── index.html : PC版のメインページ。 <br/>
　　　　:
　　└── sp <br/>
　　　　├── index.html : スマホ版のメインページ。 <br/>
　　　　:
└── 2022 : 2022年度のディレクトリ。2021年度と基本構造は同じ。<br/>

(*1) : そもそも他に書き込み可能なディレクトリが"tmp"しかありません。これはファイルの一時保存などで使えますが、基本使いません。
(*2) : 正確にはシンボリックリンクといい、ショートカットのようなもの。
  .htaccessによるPC版/スマホ版の振り分けがうまくいっていないとき用の保険。
  サーバに入り、[lnコマンド](https://qiita.com/takuyanin/items/3682ac19bbbc21792849)で設定できます。
  サーバに入る方法については後述。

#### .htaccessについて

[ここ](https://qiita.com/sanogemaru/items/7e5bd6e8dc9b04c9978e)とかが分かりやすい。</br>
テスト時にBasic認証を掛けたり、httpをhttpsにリダイレクトしたり、pc版ページとsp版ページの振り分けをしたりします。

#### Basic認証と.htpasswdについて

公開前に実際にサーバにデータを上げて動作確認をします。</br>
HP係以外の人にも見てもらいますが、この時点では来場者に見られたくない！...という場合にBasic認証を掛けます。</br>
ユーザ名とパスワードでログインする単純な奴です。</br>
ただこのタイミングで見に来る人はそう多くないと思うので、必須ではありません。</br>
掛けない場合は、見られて困る情報(パスワード、不要な個人情報など)が乗っていないかどうか手元でチェックしましょう。

#### advanced: サーバに入る

シンボリックリンクの書き換えは、サーバに入ってやる必要があります。</br>
サーバなどのリモートコンピュータと通信するための[ssh](https://ja.wikipedia.org/wiki/Secure_Shell)というプロトコルがあり、
Linux環境では、[sshコマンド](https://qiita.com/chihiro/items/c24fcbd82d1d8833e497)でサーバに入れます。</br>
パスワード認証なので、各自のコンピュータ側での設定は要りません。</br>
Macでもほぼ同じはずです。

#### advanced: 一括アップロード

ファイルのアップロードはできますが、フォルダのアップロードはコントロールパネルからはできません。</br>
sshによりファイルを転送する[scpコマンド](https://qiita.com/chihiro/items/142ebe6980a498b5d4a7)を使えば、ディレクトリごとコピーして送ることができますが、
そこまで階層も多くないので、フォルダごとにアップロードするのでいいと思います。
