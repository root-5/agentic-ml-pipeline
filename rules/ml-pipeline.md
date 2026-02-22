# 機械学習パイプライン

機械学習パイプラインはこのリポジトリで達成したい基本的な流れになります。

## ディレクトリ構造

`project/` 配下が Kaggle コンペなどの各プロジェクトごとの作業ディレクトリになります。

```txt
project/
├── reports/         # レポート
│   ├── experiment/  # 過去の実験結果 ([番号]-[アプローチの概要] で命名、例: `01-tfidf-randomtree.md`)
│   ├── summary.md   # プロジェクト全体のサマリー
│   ├── eda.md       # 探索的データ解析結果の報告書
│   └── task.md      # タスク管理用
│
├── src/                            # 約ステップごとのまとまり、各モジュールの呼び出し元
│   ├── 01_eda.ipynb                # EDA、基本的にローカル用
│   ├── 02_data_cleaning.ipynb      # データクレンジング、欠損値補完
│   ├── 03_main.ipynb               # 特徴エンジニアリング、学習、検証
│   └── modules/                    # 再利用を意識して切り出した py ファイル群、実行は ipynb からの呼び出しに限定
│       ├── data_cleaning.py        # データクレンジング、欠損値補完
│       ├── feature_engineering.py  # 特徴量エンジニアリング
│       ├── train.py                # 学習
│       └── validate.py             # 検証
│
├── input/     # 元データ、gitignore 対象
├── data/      # 加工済みデータやモデル、gitignore 対象
├── outputs/   # 提出ファイル、gitignore 対象
└── README.md  # プロジェクト概要、コンペのルール、評価指標などを記載
```

## 具体的な流れ

1. ユーザーが `project/input` ディレクトリにデータセットを配置
2. EDA
   1. エージェントが `project/src/01_eda.ipynb` を生成し EDA (探索的データ解析) を実行
   2. エージェントが結果の詳細を `project/reports/eda.md` に保存
   3. ユーザーが 2.1~2.2 を納得するまで繰り返す
3. 前処理_1 (データクレンジング、欠損値補完)
   1. エージェントが `project/src/02_data_cleaning.ipynb` を生成し前処理を実行
   2. エージェントが前処理後のデータセットを `project/data/[元データ名]-cleaned.csv` に保存
   3. ユーザーが 3.1~3.2 を納得するまで繰り返す
   4. エージェントが最終的な実装の総括を `project/reports/summary.md` に転記
4. エージェントが `project/reports/summary.md` を元に前処理・モデリング計画を立案、ユーザーの承認を得る
5. 実験ブランチ `exp/[番号]-[アプローチの概要]` を作成・チェックアウト
6. 前処理_2 (特徴量エンジニアリング)
   1. エージェントが `project/src/03_main.ipynb` を生成し前処理を実行
   2. エージェントが前処理後のデータセットを `project/data/[元データ名]-feature_engineered.csv` に保存
   3. エージェントが結果のログを `project/reports/experiment/[番号]-[アプローチの概要].md` に保存
7. モデリング
   1. エージェントが `project/src/03_main.ipynb` を編集しモデリングを実行
   2. エージェントが学習済みモデルを `project/data/model.pkl` に保存
   3. エージェントが結果のログを `project/reports/experiment/[番号]-[アプローチの概要].md` に保存
8. 検証
   1. エージェントが `project/src/03_main.ipynb` を生成し検証を実行
   2. エージェントが結果のログを `project/reports/experiment/[番号]-[アプローチの概要].md` に保存
9. エージェントがユーザーに 6. へ戻って再調整するか、終了するかを確認
10. エージェントが `project/reports/experiment/[番号]-[アプローチの概要].md` のログを元に `project/reports/summary.md` に次の実験への布石として最終総括を記載
11. PR を作成
