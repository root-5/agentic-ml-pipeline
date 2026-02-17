# Feature Engineering

## 概要 (Description)
モデルの性能を向上させるために、既存のデータから新しい特徴量を作成する。

## 手順 (Procedure)
1.  **ドメイン知識の適用**: ビジネスロジックに基づいた特徴量作成。
2.  **変換**: 対数変換、Box-Cox変換、標準化/正規化。
3.  **エンコーディング**: One-Hot Encoding, Label Encoding, Target Encoding.
4.  **相互作用**: 変数間の掛け合わせ、割り算。
5.  **集約**: グループごとの統計量（平均、最大、最小、分散など）の算出。
6.  **時系列特徴量**: ラグ特徴量、移動平均など（時系列データの場合）。

## 使用ツール・ライブラリ (Tools)
- pandas, numpy, scikit-learn

## 成果物の保存場所 (Artifacts)
- Notebooks: `notebooks/03_feature_engineering.ipynb`
- Data: `data/processed/features.csv` (or parquet)
