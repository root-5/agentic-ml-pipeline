---
name: modeling
description: 機械学習モデルを構築し、学習させる。
---

# Modeling

## 概要
機械学習モデルを構築し、学習させる。

## 手順
1.  **モデル選択**: 問題設定（回帰、分類など）に適したアルゴリズムの選定 (LightGBM, XGBoost, CatBoost, NN, etc.)。
2.  **データ分割**: Train/Validation/Testへの分割。Time Series SplitやStratified K-Foldなど適切な戦略を選択。
3.  **ハイパーパラメータチューニング**: Optunaなどを用いたパラメータ探索。
4.  **学習**: モデルのトレーニング (`model.fit`)。
5.  **保存**: 学習済みモデルの保存。

## 使用ツール・ライブラリ
- scikit-learn
- lightgbm, xgboost, catboost
- optuna

## 成果物の保存場所
- 特徴エンジニアリング、学習、検証用ノートブック: `project/src/03_main.ipynb`
- 特徴エンジニアリング用コード: `project/src/modules/feature_engineering.py`
- 学習用コード: `project/src/modules/train.py`
- 検証用コード: `project/src/modules/validate.py`
- 学習済みモデル: `project/data/model.pkl`
- 実験結果ログ: `project/reports/experiment/[番号]-[アプローチの概要].md`
