---
name: validation
description: 構築したモデルの性能を評価し、汎化性能を確認する。
---

# Validation

## 概要 (Description)
構築したモデルの性能を評価し、汎化性能を確認する。

## 手順 (Procedure)
1.  **指標計算**: Accuracy, Precision, Recall, F1-score, RMSE, AUC, LogLossなど、タスクに適した評価指標を計算。
2.  **Cross Validation**: 交差検証によるスコアの安定性確認。
3.  **残差分析**: 予測値と実測値の誤差分布を確認。
4.  **特徴量重要度**: Feature ImportanceやSHAP値による寄与度の確認。
5.  **Error Analysis**: 誤分類・大誤差サンプルの定性的な分析。

## 使用ツール・ライブラリ (Tools)
- scikit-learn (metrics)
- matplotlib, seaborn (confusion matrix, ROC curve)
- shap

## 成果物の保存場所 (Artifacts)
- Notebooks: `notebooks/05_validation.ipynb`
- Reports: `output/reports/validation_result.md`
