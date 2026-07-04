# Soccer Match Prediction

筑波大学「機械学習とパターン認識」最終レポート実装．  
European Soccer Database を用いて，サッカー試合結果（ホーム勝利・引き分け・アウェイ勝利）の予測可能性を検証する．

## 概要

市場オッズ・直近成績・スタメン選手レーティングを特徴量として，3クラス分類モデルを構築・比較した．

- **データ**: [European Soccer Database](https://www.kaggle.com/datasets/hugomathien/soccer)（Kaggle）
- **対象**: ヨーロッパ主要11リーグ，2008〜2016年，約20,000試合
- **タスク**: 試合結果の3クラス分類（H / D / A）

## 特徴量

| カテゴリ | 特徴量 | 内容 |
|---|---|---|
| 直近成績 | `home/away_avg_gf/ga/pts` | 直近5試合の平均得点・失点・ポイント |
| 市場オッズ | `B365H / B365D / B365A` | Bet365 の勝敗オッズ |
| 選手レーティング | `home/away_avg_rating` | スタメン11人のFIFA評価値平均 |

## モデルと結果

| モデル | Accuracy | Log Loss |
|---|---|---|
| Logistic Regression | **0.537** | 0.971 |
| Random Forest | 0.507 | 1.016 |
| XGBoost | 0.500 | 1.016 |
| Home Win Baseline | 0.459 | — |
| Random Baseline | 0.323 | — |

## 実行方法

Google Colab での実行を推奨．

1. Kaggle API キーを取得し，Colab の環境変数または `/root/.kaggle/kaggle.json` に設置する
2. `soccer_prediction.ipynb` を Colab で開く
3. セルを順番に実行する（データのダウンロードから前処理・学習・評価まで一括実行）

## ファイル構成

```
.
├── soccer_prediction.ipynb   # メインノートブック
└── README.md
```

## 依存ライブラリ

```
pandas, numpy, scikit-learn, xgboost, matplotlib, seaborn, kaggle
```