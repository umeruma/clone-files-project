# GDrive Files Project

Google Drive からローカルにファイルコピーするプロジェクト

## ユースケース
- ミーティングの文字起こしファイル（`.txt`）を Google Drive からローカルにダウンロードして、LLMの参照元フォルダとして利用する。

## 使い方

```bash
# Google Drive から transcripts/ 指定フォルダからファイルをダウンロード
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

### 2. rclone をインストール、Google Drive との接続を設定する。

前置き: rcloneの公式ドキュメント [Making your own client_id](https://rclone.org/drive/#making-your-own-client-id) にある通り、自分で client_id と client_secret を用意するのがベストプラクティス

Google Drive をremoteドライブ `drive-work` として設定。 
（mise.tomlの `RCLONE_REMOTE` に対応していれば別名でも問題ない）

### 3. .env ファイルの準備

1PasswordのEnvironments機能を利用するのが良さそう。

mise.toml と同じディレクトリに `.env` ファイルを作成し、以下の環境変数を追加

```
GDRIVE_FOLDER_ID=<folder_id>
# ex. フォルダを開いたURL https://drive.google.com/drive/u/0/folders/<folder_id> から <folder_id> だけを抜き出して指定する
```
