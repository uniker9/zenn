---
title: "学習メモ：機械学習＆ディープラーニングのしくみと技術がしっかりわかる教科書"
emoji: "🗒"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["machine learning"]
published: true
---

## Chapter 3. 機械学習のプロセスとコア技術

### 20. 能動学習

#### 受動学習

全データを使用する。

#### 能動学習

1 .まぎらわしいデータを選ぶ。
2. 正解データを付与する（ラベル付けする）。
3. 学習させる。
21. 相関と因果

#### 因果分析におけるガイドライン

* 強固性
* 一致性
* 特異性
* 時間的先行性
* 量-反応関係
* 妥当性
* 整合性
* 実験
* 類似性
* 回帰分断デザイン

---

## Chapter 4. 機械学習のアルゴリズム

### 23. 回帰分析

測定値（真値） $y^{\ast}_{\rm i}$ に対する理論値（回帰による推定値）を $g_{\rm i} := g ( \vec{x}^{( \rm i )} ) = \vec{w} \cdot \vec{x}^{(\rm i)}  + b$ と表すとき、損失関数（誤差関数）$d( \{ \vec{x}^{(\rm i)} | i = 1,2,...,N\} )$ は、

$$
d(\{ \vec{x}^{(\rm i)} | i = 1,2,...,N\} ) = \sum_{i=1}^{N} | y^{\ast}_i - g(\vec{x}^{(\rm i)})  |^2 +  || \vec{w} || = || \vec{y} - \vec{g} ||_2 + || \vec{w} ||
$$

#### L1正則化：ラッソ回帰

罰則項（正則化項） $|| \vec{w} ||$ として $|| \vec{w} ||_1$ を使うものを L1正則化と呼び、L1正則化を用いる線形回帰をラッソ回帰と呼ぶ。

#### L2正則化：リッジ回帰

罰則項（正則化項） $|| \vec{w} ||$ として $|| \vec{w} ||_2$ を使うものを L2正則化と呼び、L2正則化を用いる線形回帰をリッジ回帰と呼ぶ。

#### Elastic Net 回帰

L1正則化もL2正則化も用いる回帰。


### 24. サポートベクターマシン（SVM）

#### ソフトマージンSVM

境界の向こう側のデータを許容するもの。

#### カーネル法

高次元特徴空間へ写像してから線形分離する方法。

カーネル関数には、

* ガウシアン（RBF）カーネル
* 多項式カーネル

### 26. アンサンブル学習

#### バギング

母集団から重複込みでランダムにデータを抽出する **ブートストラップ法** を使って、全データから訓練データ群を複数セット取り直し、それぞれのデータ群から学習モデルを作る。それら複数の学習モデルによる予測結果を掛け合わせて予測する。

#### ブースティング

学習させてモデル1を作り予測を行い、間違えた部分を再学習させたモデル2を作り予測を行い、また間違えた部分を再学習させてモデル3を作り予測を行い……これらできあがったモデル1,2,... の予測結果をかけ合わせて予測する。


* AdaBoost：2クラスの分類に用いられる。
* SAMME（Stagewise Additive Modeling using a Multiclass Exponential loss function）：3クラス以上。


### 27. アンサンブル学習の応用

#### ランダムフォレスト

バギングの派生。特徴量ごとランダムに取り直す。

#### スタッキング

予測結果を入力して予測する。

#### 勾配ブースティング

誤差の予測、またその誤差の予測…を重ねる。

### 29. ベイジアンモデル

データがどのように発生しているのかというデータの発生構造（モデル）の候補をあらかじめ設計しておき、データを使ってそのモデルを推定し、推定したモデルをもとに予測を行う。

### 30. 時系列分析と状態空間モデル

#### 基本の時系列モデル

##### 自己回帰（AR）

##### 移動平均（MA）

##### 自己回帰移動平均（ARMA）

##### 自己回帰和分移動平均（ARIMA）

上昇や下降といったトレンドの影響を抑えるために、データの差分をとる。

##### 季節自己回帰和分移動平均（SARIMA）

季節変動（周期的変動）をデータから差し引く。

### k近傍（k-NN）法と k平均（k-means）法

#### k近傍法：分類に利用される教師あり学習のアルゴリズム

学習データ（正しいラベルを付与したデータ）を用意する。
分類したいデータと、学習データの距離を計測する。
距離の短い（類似度の高い）データを $k$ 個取り出し、多数決で分類する。
性能のよい $k$ を選ぶ。

#### k平均法：クラスタリングに利用される教師なし学習のアルゴリズム

データをランダムに $k$ 個のクラスタに分ける。
クラスタ毎に重心を求める。
もっとも近い重心のクラスタに分け直す。
新たな重心を求める。
収束するまで繰り返す。

---

## Chapter 5. ディープラーニングの基礎知識

---

## Chapter 6. ディープラーニングのプロセスとコア技術

### 37. 誤差逆伝搬法によるニューラルネットワークの学習

#### 誤差逆伝搬法（バックプロぱゲーション）

### 38. ニューラルネットワークの最適化

#### 最適化アルゴリズム

##### SGD（確率底勾配降下法）

##### Momentum SGD

##### Adagrad

##### RMSprop

##### Adam


### 40. 転移学習

#### ドメイン適合

#### ドメイン混同（domain confusion）

#### One-shot 学習

#### 公開データセットと学習済みモデル

* [MNIST](https://www.atmarkit.co.jp/ait/articles/2001/22/news012.html) : 手書き数字
* MS-COCO
* ImageNet
* Open Images Dataset
* VisuaQA
* The Street View House Numbers (SVHN)
* IFAR-10
* [Fashon-MNIST](https://github.com/zalandoresearch/fashion-mnist) : 衣料品

---

## Chapter 7. ディープラーニングのアルゴリズム

### 42. 再帰型ニューラルネットワーク（RNN）

#### Long Short Term Memory (LSTM)

#### Gated Recurrent Unit (GRU)

#### 双方向RNN (Bidirectional RNN)

#### sequene to sequence (Seq2Seq)

#### Attention

Encorder の途中の状態も Decorder に入力する。

#### Transformer

* Encorder-Decorder の構造を持つ。
* Attention 機構を持つ。
* RNN は使っていない。

#### ELMo (Embeddings from Language Models)

#### BERT (Bidirectional Encoder Representations from Transformers)

### 43. 強化学習とディープラーニング

必要なサンプル数は、モデルベース、価値ベース、方策ベースの順に多くなる。

* モデルベース
  * モデルは既知
    * AlphaZero
  * モデルを学習
* モデルフリー
  * 価値ベース（Q学習）：行動の選択肢が有限少数の場合
    * DQN
  * 方策ベース（方策最適化）
    * 方策勾配法 (Policy Gradient)
      * REINFORCE
  * 価値ベースと方策ベースの組合せ
    * Actor-Critic

#### 参考リンク

* [深層強化学習アルゴリズムまとめ@shionhonda](https://qiita.com/shionhonda/items/ec05aade07b5bea78081)

* [東京大学松尾研 深層強化学習サマースクール](https://twitter.com/ImAI_Eruel/status/1303677795806056451?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1303677795806056451%7Ctwgr%5E%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fqiita.com%2Fshionhonda%2Fitems%2Fec05aade07b5bea78081)

#### DQN (Deep Q-Network)

（状態、行動） -> 行動価値 の対応付けの表を代替するニューラルネットを学習させる。
出力した行動価値にしたがって行動を選択する。
基本的には行動価値最大の行動を選択するが、まれに（確率 $\epsilon$ で）ランダムな選択をする。このような選択を $\epsilon$ -greedy 法と呼ぶ。

#### Actor-Critic

方策ベースの Actor と価値ベースの Critic 

* A2C (advantage Actor-Critic) : 同期並列高速化アルゴリズム
* A3C (asynchronous advantage Actor-Critic) ：非同期並列高速化アルゴリズム

### 44. オートエンコーダ

符号化復号化で入力データと同一データを出力できることを目指す。
符号化後のデータにはそのデータの本質的な情報が表されていると考えられる。
これを **潜在変数** と呼び、次元削減に活用できる。

#### CAE (Convolutional Autoencoder)

#### DAE (Denoising Autoencoder)

#### VAE (Variational Autoencoder)

中間層で平均と分散を出力し、それらを用いて入力データと条件を変えた新たなデータを出力する。

### 45. GAN（敵対的生成ネットワーク）

学習時の不安定さがネック。

#### 生成器 (Generator)

#### 識別器 (Discriminator)

#### モード崩壊

生成データが偏ること。

### 46. 物体検出

近年の物体検出アルゴリズムは、注目領域決定とラベル推定を1つのニューラルネットワークで行う。

手法 | 識別制度 | 処理速度
--- | --- | ---
Faster R-CNN | ◎ | △
SSD | ◯ | ◯
Yolo | △ | ◎


#### Faster R-CNNN

#### SSD

#### Yolo


