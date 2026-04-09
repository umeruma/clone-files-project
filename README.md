# GDrive Files Project

Google Drive からローカルにファイルコピーするプロジェクト

## ユースケース
- ミーティングの文字起こしファイル（`.txt`）を Google Drive からローカルにダウンロードして、LLMの参照元フォルダとして利用する。

## 使い方

`.env` ファイルに `GDRIVE_FOLDER_ID` を指定した上で、以下のコマンドを実行

```bash
# mise.toml の LOCAL_DEST に指定されているフォルダにファイルをダウンロード
mise run download

# Google Drive フォルダをブラウザで開く
mise run open
```

## セットアップ

必要なツール

- [mise](https://mise.jdx.dev/)
- [rclone](https://rclone.org/)

### 1. mise をインストール

[公式ドキュメント](https://mise.jdx.dev/)を参考にインストール

### 2. rclone をインストール、リモートドライブに利用しているGoogle Driveを設定

```
brew install rclone
```

もしくは、[公式ドキュメント](https://rclone.org/install/)を参考にインストール。

Google Drive をremoteドライブ `drive-work` として設定（mise.tomlの `RCLONE_REMOTE` に対応していれば別名でも問題ない）

注意: rcloneの公式ドキュメント [Making your own client_id](https://rclone.org/drive/#making-your-own-client-id) にある通り、自分で client_id と client_secret を用意するのがベスト

### 3. .env ファイルの準備

[1PasswordのEnvironments機能](https://developer.1password.com/docs/environments/)を利用するのがオススメ

mise.toml と同じディレクトリに `.env` ファイルを作成、以下の環境変数を追加

```
GDRIVE_FOLDER_ID=<folder_id>
# フォルダを開いたURL https://drive.google.com/drive/u/0/folders/<folder_id> folder_id部分を抜き出して指定
```
