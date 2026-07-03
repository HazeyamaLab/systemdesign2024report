# 【🪟Windowsセルフホスト用】開発コンテナーの作成・使用方法

## 🧭 Quick Links

- [作業を再開する](#-作業を再開するには)
- [作業を終了する](#-作業を終了するには)

## 👉 開発コンテナーの作成手順

> [!NOTE]
> 以降の説明は、[必要なソフトウェアのインストール](https://github.com/HazeyamaLab/systemdesign2024/blob/main/docs/setup/procedure-for-selfhost-windows.md)が完了していることを前提としています。

1. Docker DesktopとVSCodeを起動します。
2. VSCode上で開発コンテナーを作成するために`Dev Containers`拡張機能をインストールします。`Ctrl+Shift+P`（`Ctrl`キーと`Shift`キーを押しながら`P`キーを押す）を押してコマンドパレットを開き、**`>`を消してから**`ext install ms-vscode-remote.remote-containers`と入力して`Enter`キーを押します。
3. 開発コンテナーを作成します。
    1. `Ctrl+Shift+P`を押してコマンドパレットを開き、`Dev Containers: Clone Repository in Container Volume`と入力して`Enter`キーを押します（途中まで入力して同名の項目を選択しても構いません）。
    2. 入力欄に`https://github.com/HazeyamaLab/systemdesign2024report`と入力して`Enter`キーを押します。（このURLをコピーするためにVSCode以外のウィンドウを触ると、コマンドパレットが閉じられてしまうので、注意してください）
    3. 開発コンテナーの作成が完了するまで待ちます。開発コンテナーの作成には数分間かかることがあります。作成に成功すると自動的に開発コンテナーに接続され、ウィンドウ左下のリモートボタンに`Dev Container: systemdesign2024report`と表示されます。

> [!NOTE]
> 過去にWSLでUbuntuを利用していた場合、`An error occured setting up the container`（`コンテナーの設定中にエラーが発生しました`）というエラーが発生し、開発コンテナーの作成に失敗することがあります。
> その場合は、[VSCodeの設定「dev.containers.mountWaylandSocket」](vscode://settings/dev.containers.mountWaylandSocket)の値を`false`にしてください（チェックを外してください）。

## ℹ️ 開発環境の使用方法

このページにはご自身のPC上で作成した開発コンテナー特有の事柄を記します。それ以外の事柄は[README.md](../../README.md#ℹ️-開発環境の使い方)をご覧ください。

### 🧐 作業を終了するには？

VSCodeと開発コンテナーの接続を切断します。VSCodeのメニューバーの`File`（`ファイル`）→`Close Remote Connection`（`リモート接続を閉じる`）をクリックします。その後、VSCodeのウィンドウを閉じてVSCodeを終了します。

### 🧐 作業を再開するには？

Docker Desktopを起動してからVSCodeを開発コンテナーに接続します。

1. Docker DesktopとVSCodeを起動します。
2. VSCodeのウィンドウ左側の`Remote Explorer`（`リモート エクスプローラー`・`🖥️`のようなアイコン）をクリックして、リモートエクスプローラーを表示します。
3. `Remote (Tunnel/SSH)`（`リモート (トンネル/SSH)`）の一覧が表示されている場合は、プルダウンで`Dev Containers`（`開発コンテナー`）の一覧を表示するように切り替えます。
4. `Dev Containers`（`開発コンテナー`）の一覧から`systemdesign2024report_devcontainer-devcontainer-1`を選び、`→`（`Open Container in Current Window`、`現在のウィンドウのコンテナーで開く`）または`Open Container in New Window`（`新しいウィンドウのコンテナーで開く`）をクリックします。
5. 開発コンテナーへの接続に成功すると、ウィンドウ左下のリモートボタンに`Dev Container: systemdesign2024report`と表示されます。
6. `mysql`コンテナーや`adminer`コンテナーの機能を利用する場合は、`Other Containers`の一覧の`systemdesign2024report_devcontainer-mysql-1`および`systemdesign2024report_devcontainer-adminer-1`が起動していることを確認します。
    - 起動している場合は`▶️`のようなアイコンが付いています。
    - 起動していない場合は右クリック→`Start Container`（`コンテナーの開始`）をクリックします。

### 🧐 Docker Desktopを起動しているのに開発コンテナーにVSCodeを接続できない

作業を再開しようとしてVSCodeの開発コンテナーの一覧を確認しても開発コンテナーが表示されなかったり、`Docker からエラーが返されました。Docker デーモンが実行されていることを確認します。`と表示されたりすることがあります。

この場合、Docker Desktopが休止状態になっている可能性があります。
休止状態から復帰するには、スタートメニューからDocker Desktopを起動するなどして、Docker Desktopのウィンドウをもう一度開いてください。

### 🧐 Docker DesktopおよびWSLを終了するには？

1. Docker Desktopを終了します。タスクバーの通知領域の`Docker Desktop`のアイコンを右クリック→`Quit Docker Desktop`をクリックします。
2. Docker Desktopが終了したのを確認してからWSLを終了します。ターミナルまたはPowerShellでコマンド`wsl --shutdown`を実行します。

### 🧐 開発コンテナーに割り当てられているメモリが足りない。「`Reconnecting to Devcontainer…`」が頻発する。

- WSL Settingsで、WSLが使用できるメモリのサイズの上限を引き上げてください。WSL Settingsの変更を反映するには、一度[Docker DesktopとWSLを終了する](#-docker-desktopおよびwslを終了するには)必要があります。
- また、不要な拡張機能を無効化するのも効果的です。
    1. VSCodeのウィンドウ左側の`Extensions`（`拡張機能`）をクリックします。
    2. `Dev Container: …`内の以下の拡張機能を右クリック→`Disable`（`無効にする`）をクリックします。
        - Gradle for Java
        - ESLint
        - Maven for Java
