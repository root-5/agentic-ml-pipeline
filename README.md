# agentic-ml-pipeline

AI を活用した機械学習パイプラインの自動化の仕組み構築を目指します。
単純に AutoML 系ツールを使うのではなく、利用者のドメイン知識、発想なども活かせる形で設計します。

また、副次的な取り組みとしてシンプルかつ拡張性のある AI 開発体制を構築します。

## AI 開発体制

最初は以下の構成とする。必ず以下の棲み分けを徹底する。

```txt
agentic-ml-pipeline/
├── agents/           # エージェント定義。従業員のマネジメントのイメージで「役割・作業原則・作業パターン・作業完了条件」を定義。
├── skills/           # スキル定義。社内ドキュメントのイメージで「ドメイン知識・手順書・ツール使用法」を定義。
└── rules/            # ルール定義。社則のイメージで「全てのエージェント・どんなスキル領域でも従うべき規則」を定義。
```

また、ここが汚れると全てのエージェントの動作に影響するため、これらのディレクトリ配下では、以下のルールを徹底する。

- シンプルかつミニマル
- 読み手に依存しない明瞭な記述
- 「とりあえず追加しとく」といった判断は絶対に避け、とにかく最低限から始める

## 機械学習パイプライン

詳細は [ml-pipeline.md](rules/ml-pipeline.md) を参照。

### 基本構成

以下のツール・ライブラリを仕様する。

- uv
- optuna
- Kaggle Notebook

### 原案との違い

- Obsidian, Zettelkasten, Kaggle, タスク管理にモジュール化し、コアである AI ベースのモデル作成パイプライン機能とは疎結合にする
- markdown フォーマッターの導入
- Optuna 導入

## 環境構築

1. uv のインストール `curl -LsSf https://astral.sh/uv/install.sh | sh`
2. uv 同期 `uv sync`
3. Kaggle Notebook の設定
   1. ブラウザの Kaggle の左メニューの「Create」を押下し、「Notebook」を選択、エディタ等が開く
   2. 右メニューの「Add Input」から参加したいコンペ名を検索して追加
   3. 任意の Notebook 名を設定する
4. Kaggle ローカル環境の設定
   1. `cd project`
   2. Kaggle API を使ってカーネルをメタデータ付きでダウンロード `uv run kaggle kernels pull [user名]/[Notebook名] -p project/src/ -m`
   3. Kaggle API を使ってメタデータからコンペ情報を取得、一時的な環境変数に保存 `export COMPETITION_NAME=$(grep -ozP '"competition_sources"\s*:\s*\[\s*\K"[^"]+' project/src/kernel-metadata.json | tr -d '"\0')`
   4. Kaggle API を使ってメタデータからコンペ情報を取得、入力データをダウンロード `uv run kaggle competitions download $COMPETITION_NAME -p project/input/`
   5. unzip して展開、zip の削除 `unzip project/input/$COMPETITION_NAME.zip -d project/input/$COMPETITION_NAME && rm project/input/$COMPETITION_NAME.zip`

### 初期構築時

1. uv 初期化 `uv init`
2. ライブラリインストール
   1. `uv add ipykernel`
   2. `uv add numpy`
   3. `uv add pandas`
   4. `uv add kaggle`
