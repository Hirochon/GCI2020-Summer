# “Home Credit Default Risk” from Kaggle
第二回もKaggleコンペ。データのカラム数が一気に増えたので、苦戦しそう…。そんな面持ちで挑み始めました。
> https://www.kaggle.com/c/home-credit-default-risk/overview/description

## 結果
#### 順位: 3位
#### Private LB: 0.76102, Public LB: 0.768, CV: 0.735

## Model
- LightGBM Single Model
- 数値はそのまま。カテゴリ変数はOHE。
- https://github.com/Hirochon/GCI2020-Summer/blob/master/Competition1/Best_model.ipynb

## やったこと

- EDA
  - カラム別でTargetとの相関や割合をすべて可視化
  - Pandas Profiling
- One Hot Encoding
  - Label Encodingよりよかった
- KaggleのNotebookを参考にした。
  - https://www.kaggle.com/cdeotte/titanic-wcg-xgboost-0-84688
- 上記NBはRで書かれていたので、なんとなくの外観理解でモデルを作成していく。
  - もっと読み込めばよかったと後々後悔
  - 名字による家族(trainで全員生きてたらtestで全員生きてるなど)を使った特徴量の作成
- XGBoostにValidation無しでぶち込む。
  - Validationをすると過学習気味に感じたので使わず。(他入賞者も同じことを言っていた。)
- 多種モデルで実験も
  - GBDT系
  - Random Forest
  - ↑Ensembleなどなど

## 反省点
- 機械学習モデルを使わずとも、上記NBのルールベースのみで入賞されている方もいらっしゃって、自分の英語やR言語に対しての苦手意識を自覚した。もっと頑張らねば。
