# “Titanic: Machine Learning from Disaster” from Kaggle
第一回コンペはKaggleのTitanicコンペ。一度チュートリアルとしてやったことはあったけれど、しっかりやる日が来るとはっっ。そんな心持ちで始めたのを覚えてます！

## 結果
#### 順位: 6位
#### Public LB: 3位, Kaggle LB: Top2%

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
