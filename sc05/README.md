#セクション5 データから特徴量へ

## データから識別まで
1. データ取得  
  ・画像、信号、検査項目、センサ出力
1. 特徴量抽出  
  ・数値、特徴量ベクトル
1. 特徴選択
1. 特徴変換
1. 正規化
1. 識別

## データクリーニング
欠損値や外れ値をクリーニングすることで、学習の精度を高める。
- 外れ値を除外する
- 欠損値を除外するか、平均値や中央値で置き換える(外れ値は先に除外)  
  sklearn.preprocessing.Imputer

## 特徴抽出
### テキストデータの特徴抽出
テキストデータの特徴をベクトルで表現する。特徴の抽出方法は、研究対象として論文が多数発表されている。  
一般的な抽出方法はscikit-learnにも予め用意されている。
- sklearn.feature_extraction.text.CountVectorizer  
  テキストデータに含まれる単語の個数を特徴量として表現する

###  画像データの特徴抽出
画像データの特徴抽出手法のひとつとして、ヒストグラムへの変換がある。  
縦軸を画素数、横軸を輝度(0-255)としてそれぞれの輝度で何画素あるか表し、RGBの3チャンネルを横に結合する。  
縦軸は、画素数が異なる画像だと比較ができないため、正規化（L１ノルム)する。

## 特徴選択
識別に有効な特徴のみを選択する（有効でない特徴(ランダムな値、定数など)を外す）
- SelectKBest
- chi2 (カイ二乗検定)

## 特徴変換
いまある特徴から、新しい特徴に変換する
* 有用な特徴に重みをつける
* 有用な特徴を足し合わせて、新たな特徴量を作る
* 相関のある特徴を回転させ、次元削減する→PCA

pandasを利用して各特徴量の相関を確認
### 線形特徴変換
- PCA(Principal component analysis 主成分分析:相関のある特徴(線形)を回転させ、次元削減する)

### 非線形特徴変換
- PolynomialFeatures(特徴量同士を乗算し、新たな特徴量を作成する)

## 標準化
特徴量毎でバラバラのスケールを揃える。  
スケールがバラバラの場合、相対的にスケールの小さい特徴が反映されないなどの問題がある。  
スケールを揃えることで、識別器の性能を向上することができる。  

### Standardization
- sklearn.preprocessing.StandardScaler(平均０、標準偏差１に変換)

### スケーリング
最大最小をある範囲におさえてしまう。外れ値がなければ有効な効果が得られる。
-  sklearn.preprocessing.MinMaxScaler

### 正規化（正則化）
各サンプル(特徴量が30個あれば30次元ベクトル)のノルムが１になるように正規化する。  
単体で使っても性能が出ることは少なく、標準化やスケーリングなどと組み合わせて使うことが多い。  
（各特徴量のスケールが異なる状態で正規化を行っても、結果に偏りがでてしまう）  
-  sklearn.preprocessing.Normalizer

### 白色化
相関をなくす、という意味。それぞれの特徴量を平等に扱うために行う。
#### PCA白色化
PCA（主成分分析）を行う時に、主成分軸側について平均0分散1にする（ぎゅっと縮める）  
利用するときは、「PCA)whiten=true)」で白色化できる

#### ZCA白色化
PCA白色化に一手間加えたような手法。  
DeepLearningで画像認識を行うときなどによく使われる手法。  
PCA白色化した値に、PCA主成分（pca.components_)を内積演算(dot)することで、元データの主成分傾きを保って白色化を行う。  
PCA白色化よりも性能がでる前処理方法として、よく使われている。
