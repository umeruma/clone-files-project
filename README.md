# GDrive Files Project

Google Drive からローカルにファイルコピーするプロジェクト

## ユースケース
- ミーティングの文字起こしファイル（`.txt`）を Google Drive からローカルにダウンロードして、LLMの参照元フォルダとして利用する。

## 使い方

[リリースページ](https://github.com/umeruma/gdrive-files-project/releases)から最新版をダウンロードして、ローカルで展開

後述のツールセットアップを済ませた上で、以下のコマンドを実行

```bash
# mise.toml の LOCAL_DEST に指定されているフォルダにファイルをダウンロード
mise run download

# Google Drive フォルダをブラウザで開く
mise run open
```

## ツールセットアップ

必要なツール

- [mise](https://mise.jdx.dev/)
- [rclone](https://rclone.org/)

### 1. mise をインストール

[公式ドキュメント](https://mise.jdx.dev/)を参考にインストール

### 2. rclone をインストール、Google Drive を追加

docs: https://rclone.org/install/

```
brew install rclone
```

#### rcloneへのドライブ追加

docs: https://rclone.org/drive/

rcloneのドキュメント ["Making your own client_id"](https://rclone.org/drive/#making-your-own-client-id) にある通り、自分で client_id と client_secret を用意するのがベスト

名前は `drive-work` とする。（mise.tomlの `RCLONE_REMOTE` に対応していれば別名でも問題ない）

### 3. .env ファイルの準備

[1PasswordのEnvironments機能](https://developer.1password.com/docs/environments/)を利用するのがオススメ

mise.toml と同じディレクトリに `.env` ファイルを作成、以下の環境変数を追加

```
GDRIVE_FOLDER_ID=<folder_id>
# フォルダを開いたURL https://drive.google.com/drive/u/0/folders/<folder_id> folder_id部分を抜き出して指定
```
