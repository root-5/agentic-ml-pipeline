# Data Cleansing

## 概要 (Description)
分析やモデリングに適した形式にデータを整形・クリーニングする。

## 手順 (Procedure)
1.  **欠損値処理**: 削除、平均値/中央値補完、予測モデルによる補完など。
2.  **異常値処理**: クリッピング、除去、変換。
3.  **データ型変換**: カテゴリ変数の適切な型変換、日付型のパース。
4.  **重複排除**: 重複レコードの確認と削除。
5.  **一貫性チェック**: 表記ゆれの統一、論理的矛盾の解消。

## 使用ツール・ライブラリ (Tools)
- pandas, numpy

## 成果物の保存場所 (Artifacts)
- Notebooks: `notebooks/02_cleansing.ipynb`
- Data: `data/interim/cleaned_data.csv` (or parquet)
