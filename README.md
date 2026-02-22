# agentic-ml-pipeline

AI を活用した機械学習パイプラインの自動化の仕組み構築を目指します。
単純に AutoML 系ツールを使うのではなく、利用者のドメイン知識、発想なども活かせる形で設計します。

また、副次的な取り組みとしてシンプルかつ拡張性のある AI 開発体制を構築します。

- [AI 開発体制の詳細](AGENT.md)
- [機械学習パイプラインの詳細](rules/ml-pipeline.md)

## 基本構成

以下のツール・ライブラリを中心に使用している。

- devcontainer
- uv
- optuna
- Kaggle Notebook

### 原案との違い

- Obsidian, Zettelkasten, Kaggle, タスク管理にモジュール化し、コアである AI ベースのモデル作成パイプライン機能とは疎結合にする
- markdown フォーマッターの導入
- Optuna 導入

## 環境構築

1. 各 VSCode 拡張機能のインストール `.vscode/extensions.json` を参照
2. devcontainer インストール後、VSCode で devcontainer を開くと自動で環境構築される
3. Kaggle Notebook の設定
   1. ブラウザの Kaggle の左メニューの「Create」を押下し、「Notebook」を選択、エディタ等が開く
   2. 右メニューの「Add Input」から参加したいコンペ名を検索して追加
   3. 任意の Notebook 名を設定する
   4. その後の Kaggle ローカル環境の設定は[こちら](skills/kaggle/SKILL.md)を参照
4. シンボリックリンクを作成して `skills/` を参照可能にする (ex. `ln -s ../skills .github/skills`)
5. `project/README.md` に今回のプロジェクトの概要やデータセット、ルールなどの情報を記載する
