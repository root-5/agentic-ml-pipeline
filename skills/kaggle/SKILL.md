---
name: Kaggle API
description: Kaggle API の基本的な使い方
---

# Kaggle API

[公式ドキュメント](https://github.com/kaggle/kaggle-api/blob/main/docs/README.md)

## 初期設定

1. Kaggle API のインストール自体は `uv sync` で完了しているはず
2. インストール確認 `uv run kaggle --help`
3. [API キーの発行](https://www.kaggle.com/settings)、json ファイルをダウンロード
4. ~/.kaggle ディレクトリを作成し、権限を設定 `mkdir -p ~/.kaggle && chmod 700 ~/.kaggle`
5. ダウンロードした json ファイルを ~/.kaggle に配置し、権限を設定 `chmod 600 ~/.project/kaggle.json`
6. カーネルをメタデータ付きで project/src/ にダウンロード `uv run kaggle kernels pull {ユーザー名}/{カーネル名} -p project/src/ -m`
7. メタデータからコンペ情報を取得、入力データを data / にダウンロード `uv run kaggle competitions download $(grep -ozP '"competition_sources"\s*:\s*\[\s*\K"[^"]+' project/src/kernel-metadata.json | tr -d '"\0') -p project/input/`
8. unzip して展開、zip の削除 `unzip project/input/{zip名}.zip -d project/input && rm project/input/{zip名}.zip`

## アップロードと提出

1. コンペの Notebook のコードを project/src/ からアップロード `uv run kaggle kernels push -p project/src/`
2. コンペの提出用ファイルをアップロード `uv run kaggle competitions submit -c $COMPETITION_NAME -f project/output/submission.csv -m "Submit from local"`
3. コンペの Notebook のコードをアップロード `uv run kaggle kernels push -p project/src/`
4. コンペの提出用ファイルをアップロード `uv run kaggle competitions submit -c $(grep -ozP '"competition_sources"\s*:\s*\[\s*\K"[^"]+' project/src/kernel-metadata.json | tr -d '"\0') -f project/output/submission.csv -m "Submit from local"`
5. Kaggle のブラウザ上で Notebook を実行結果を確認
