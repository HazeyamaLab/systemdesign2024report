# 【📡 櫨研リモート開発環境用】開発コンテナーの作成・使用方法

## 🧭 Quick Links

- [作業を再開する](#-作業を再開するには)
- [作業を終了する](#-作業を終了するには)

## 👉 開発コンテナーの作成手順

> [!NOTE]
> 以降の説明は、[必要なソフトウェアのインストール](https://github.com/HazeyamaLab/systemdesign2024/blob/main/docs/setup/procedure-for-hrde-user.md)が完了していることを前提としています。

### 1. 櫨研リモート開発環境にログインして開発コンテナーを作成する

1. [櫨研リモート開発環境](https://emerald.u-gakugei.ac.jp/)にログインします。
2. ログインに成功すると、あなたが櫨研リモート開発環境上で作成した開発コンテナーの一覧が表示されます。このページはよく使うので、ブラウザのブックマークに登録しておくことをおすすめします。
3. 開発コンテナーを作成します。
    1. 手順2の画面の右上`Create Workspace`→`開発コンテナー`をクリックします。
    2. 表示された画面に次の情報を入力します。
        - `Workspace Name`: 好きな文字列を入力してください。アルファベット大文字、アルファベット小文字、数字と`-`を使用できます。
        - `Docker レジストリのホスト名`: 今回は`https://emerald.u-gakugei.ac.jp:5000`と入力します。
        - `Docker レジストリのユーザー名`: リモート開発環境の利用者に個別で連絡します。
        - `Docker レジストリのパスワード`: リモート開発環境の利用者に個別で連絡します。
        - `Git リポジトリのオーナーの名前`: 今回は`HazeyamaLab`と入力します。
        - `Git リポジトリの名前`: 今回は **`systemdesign2024report`** と入力します。
        - `Git ブランチの名前`: 今回は`main`と入力します。
        - `devcontainer.json へのパス`: 今回は **`.devcontainer/systemdesign2024report-hrde/devcontainer.json`** と入力します。
    3. 入力が終わったら画面右下`Create Workspace`ボタンをクリックします。
4. 開発コンテナーの作成が完了するまで待ちます。開発コンテナーの作成には数分間かかることがあります。開発コンテナーの作成に成功すると、画面中央に緑色の枠が表示されます。

### 2. 作成した開発コンテナーにVSCodeを接続し、VSCodeの設定を行う

1. VSCodeを起動します。
2. VSCodeからリモート開発環境上に作成した開発コンテナーに接続するために、Coder拡張機能をインストールします。`⇧⌘P`（`⇧`キーと`⌘`キーを押しながら`P`キーを押す）を押してコマンドパレットを開き、**`>`を消してから**`ext install coder.coder-remote`と入力して`Enter`キーを押します。
3. VSCodeでCoderにログインします（ログインしていない場合のみ）。
    1. `⇧⌘P`を押してコマンドパレットを開き、`Coder: Login`と入力して`Enter`キーを押します（途中まで入力して同名の項目を選択しても構いません）。
    2. `Enter the URL of your Coder deployment`というダイアログが表示されます。入力欄に`https://emerald.u-gakugei.ac.jp`と入力して`Enter`キーを押します。
    3. ダイアログの指示に従って、ブラウザで https://emerald.u-gakugei.ac.jp/cli-auth にアクセスし、ログイン用のコードを取得するためのページを開きます。ページ中央のボタンをクリックして、ログイン用のコードをクリップボードにコピーします。
    4. VSCodeに戻り、コピーしたログイン用のコードをダイアログに貼り付けて`Enter`キーを押します。ログインに成功すると、画面右下に`Welcome to Coder`と表示されます。
4. リモート開発環境上に作成した開発コンテナーに接続します。
    1. `⇧⌘P`を押してコマンドパレットを開き、`coder.open`と入力して`Enter`キーを押します（途中まで入力して同名の項目を選択しても構いません）。
    2. `Connect to a workspace`というダイアログが表示されます。作成した開発コンテナーを選択します。
    3. `Select an agent`というダイアログが表示されます。`workspace`を選択します。
    4. 新しいウィンドウが開き、開発コンテナーに接続されます。接続に完了すると、画面左下のリモートボタンに`Coder: <作成した開発コンテナーの名前>`と表示されます。
5. 必要な拡張機能をインストールします。
    1. `Ctrl+Shift+P`（`Ctrl`キーと`Shift`キーを押しながら`P`キーを押す。macOSの場合は`⇧⌘P`）を押してコマンドパレットを開き、`Extensions: Show Recommended Extensions`と入力してEnterキーを押します（途中まで入力して同名の項目を選択しても構いません）。
    2. 画面左側の`Workspace Recommendations`（`ワークスペースの推奨事項`）の右上`Install Workspace Recommended Extensions`（`ワークスペースのおすすめの拡張機能をインストール`）をクリックします。

## ℹ️ 開発環境の使用方法

このページには櫨研リモート開発環境特有の事柄を記します。それ以外の事柄は[README.md](../../README.md#ℹ️-開発環境の使い方)をご覧ください。

### 🧐 作業を終了するには？

VSCodeと開発コンテナーの接続を切断します。メニューバーの`File`（`ファイル`）→`Close Remote Connection`（`リモート接続を閉じる`）をクリックします。その後、VSCodeのウィンドウを閉じてVSCodeを終了します。

### 🧐 作業を再開するには？

作業内容は櫨研リモート開発環境上の開発コンテナーに保存されます。
櫨研リモート開発環境の開発コンテナーにVSCodeを接続してください。

具体的には、まず、[櫨研リモート開発環境にログイン](#1-櫨研リモート開発環境にログインして開発コンテナーを作成する)してください。ログインしたら、[作成した開発コンテナーにVSCodeを接続する](#2-作成した開発コンテナーにvscodeを接続しvscodeの設定を行う)の手順3以降と同じ手順で、開発コンテナーにVSCodeを接続してください。
