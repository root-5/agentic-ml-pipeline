# agentic-ml-pipeline

AI を活用した機械学習パイプラインの自動化の仕組み構築を目指します。
単純に AutoML 系ツールを使うのではなく、利用者のドメイン知識、発想なども活かせる形で設計します。

また、副次的な取り組みとしてシンプルかつ拡張性のある AI 開発体制を構築します。

## 機械学習パイプライン

1. 利用者が `project/input` ディレクトリにデータセットを配置
2. EDA
   1. エージェントが `project/eda/src/01_[discribe].ipynb` を生成し EDA (探索的データ解析) を実行
   2. エージェントが結果のまとめを `project/eda/report/01_[discribe].md` に保存
   3. 利用者が 2.1~2.2 を納得するまで繰り返す
   4. `project/eda/report` をまとめた総括を `project/summary.md` に転記
3. 前処理_1 (データクレンジング、欠損値補完)
   1. エージェントが `project/cleansing/src/01_[discribe].ipynb` を生成し前処理を実行
   2. エージェントが結果のまとめを `project/cleansing/report/01_[discribe].md` に保存
   3. エージェントが前処理後のデータセットを `project/cleansing/output/01_[discribe].csv` に保存
   4. 利用者が 3.1~3.3 を納得するまで繰り返す
   5. `project/cleansing/report` をまとめた総括を `project/summary.md` に転記
4. `project/summary.md` を元にプランニングを実施、次の前処理・モデリング計画を立案
5. 前処理_2 (特徴量エンジニアリング)
   1. エージェントが `project/features/src/01_[discribe].ipynb` を生成し前処理を実行
   2. エージェントが結果のまとめを `project/features/report/01_[discribe].md` に保存
   3. エージェントが前処理後のデータセットを `project/features/output/01_[discribe].csv` に保存
6. モデリング
   1. エージェントが `project/modeling/src/01_[discribe].ipynb` を生成しモデリングを実行
   2. エージェントが結果のまとめを `project/modeling/report/01_[discribe].md` に保存
   3. エージェントが学習済みモデルを `project/modeling/output/01_[discribe]/model.pkl` に保存
7. 検証
   1. エージェントが `project/validation/src/01_[discribe].ipynb` を生成し検証を実行
   2. エージェントが結果のまとめを `project/validation/report/01_[discribe].md` に保存
8. エージェントが `project/summary.md` に 5.~7. の結果を追記、利用者に 4. へ戻って再調整するか、終了するかを確認
9. エージェントが終了時に `project/summary.md` に最終総括を記載

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

## 補足

### 原案との違い

- Obsidian, Zettelkasten, Kaggle, タスク管理にモジュール化し、コアである AI ベースのモデル作成パイプライン機能とは疎結合にする
- markdown フォーマッターの導入
- Optuna 導入

実行環境: Google Colab
Google Drive マウントしてデータ保存

AutoML（AutoGluon / H2O / Vertex AI）との違い

agentic-ml-pipeline/
├── agents/           # 専門エージェント
├── skills/           # ワークフロー定義とドメイン知識
├── commands/         # スラッシュコマンド
├── rules/            # 常に従うルール
└── examples/         # 設定例




optuna + finetuning
2時間 + CV
Kaggle Notebook 上