# “Home Credit Default Risk” from Kaggle
> https://www.kaggle.com/c/home-credit-default-risk/

第二回もKaggleコンペ。データのカラム数が一気に増えたので、苦戦しそう…。そんな面持ちで挑み始めました。

## 結果
#### 順位: 3位 / 261人中
#### Private LB: 0.76102, Public LB: 0.768, CV: 0.735

## 背景
顧客のデータからその顧客が債務不履行(default)になる確率を予測。データセットのTARGETカラムが目的変数、それ以外が説明変数となる。TARGETカラムが1であれば支払い困難、0であればそれ以外を表す。

## Model
- LightGBM Single Model
- 数値はそのまま。
- カテゴリ変数はOHE。
- 8Fold, StratifiedKFold.
- Optunaでのパラメータサーチ
- https://github.com/Hirochon/GCI2020-Summer/blob/master/Competition2/3rd_place_solution.ipynb

## やったこと

- EDA
  - カラム別でTargetとの相関や割合をすべて可視化
  - Descriptionがあったので、日本語訳を出しながら、意味ありそうな四則演算特徴量をを抽出していく。
- One Hot Encoding
  - Kaggleとは違い(?)、Label Encodingよりよかった
- 特徴量の作り方は特にコレを参考にしたというものはない。
- ひたすら以下ルーティーン実験の日々
  1. 四則演算特徴量を追加
  2. Optunaでパラメータチューニング
  3. CV測って、LB見つつ、相関が取れてるか見ていく
- CrossValidationについて
  - 不均衡データだったので、偏りが出ないようにStratifiedKFoldを採用
  - 他上位入賞者もほとんどこれ
  - 5Foldで最初やってたけど、10Foldは時間かかったり、testデータ少なくなるなぁと思い、間を取って8Fold
- コンペのLBについて
  - スコアが詰まっていたので、パラメーターチューニングで勝敗決まるんちゃうかコレ感でてた。
  - 実際そうでもなかったけど、特徴を作り続ける時間もなかったので、ひたすら放置でOptuna回してた。

## 反省点
- もっとKaggleのDiscussionとかNotebookとか読みに行っても良かった
- 重要となる`EXT_SOURCE`の多くが欠損してたので、埋める努力をしてみたけど、リークとなった…(バグカナ…)
- 考えられる四則演算がまだあった。(実験不足の悔い)
