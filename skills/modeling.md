# Modeling

## 概要 (Description)
機械学習モデルを構築し、学習させる。

## 手順 (Procedure)
1.  **モデル選択**: 問題設定（回帰、分類など）に適したアルゴリズムの選定 (LightGBM, XGBoost, CatBoost, NN, etc.)。
2.  **データ分割**: Train/Validation/Testへの分割。Time Series SplitやStratified K-Foldなど適切な戦略を選択。
3.  **ハイパーパラメータチューニング**: Optunaなどを用いたパラメータ探索。
4.  **学習**: モデルのトレーニング (`model.fit`)。
5.  **保存**: 学習済みモデルの保存。

## 使用ツール・ライブラリ (Tools)
- scikit-learn
- lightgbm, xgboost, catboost
- optuna

## 成果物の保存場所 (Artifacts)
- Notebooks: `notebooks/04_modeling.ipynb`
- Models: `models/[model_name].pkl`
