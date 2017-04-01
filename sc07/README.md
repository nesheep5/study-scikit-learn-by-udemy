# セクション 7 いろいろな識別器
## 識別器の種類
- Nearest Neighbors(K近傍法)
- Logistic Regression(ロジスティック回帰)
- SVM(サポートベクターマシン 線形・非線形)

## One-Vs-The-Rest(OVR)
あるクラスとそれ以外のクラスの境界を求める。多クラス問題の場合は、One-Vs-The-Restをクラス数分行う。
-http://scikit-learn.org/stable/modules/multiclass.html#one-vs-the-rest

## One-Vs-One(OVO)
あるクラスとあるのクラスの境界を求める。クラス数が多い場合、組み合わせが多くなってしまうので使用しないことが多い。
- http://scikit-learn.org/stable/modules/multiclass.html#one-vs-one

## k近傍識別器(kNN)
ある点に近い順のサンプルk点を求め多数決で決定する
- sklearn.neighbors.KNeighborsClassifier
- sklearn.neighbors.RadiusNeighborsRegressor

## パーセプトロン
ある２つのクラス群の境界を線形に求める。  
境界線の傾きと切片を少しずつ変えながら、きれいに分類できるパラメータを探す。  
分類できたら処理を打ち切るため、境界線はランダム性がある。
- sklearn.linear_model.Perceptron
キーワード
- 学習則
- 損失関数

## ロジスティック回帰
パーセプトロン同様、２クラスの境界を線形に求める。
こちらは境界線にランダム性はなく、毎回同じ線が求められる。
- sklearn.linear_model.LogisticRegression

## サポートベクターマシン(SVM)
２クラスの境界を求める。線形、非線形どちらも可能。  
境界線の両サイドにマージンをとり、それが最大となる境界線を求める。  
非線形の場合はパラメータのチューニングが複雑なので、まずは線形で求めるのがオススメ。
- sklearn.svm.SVC

## 多層パーセプトロン(MLP)
パーセプトロンを多層にしたもので、入力層、隠れ層、出力層からなる。ニューラルネットとも呼ばれる。  
ノードの数や層の数などを変更すると性能が変化する。（多ければ良いというものでもない）
- sklearn.neural_network.MLPClassifier

## ランダムフォレスト
決定木を複数組み合わせて分類を行う。  
木の数を増やすと複雑な境界線を引くことができるが、増やしすぎると複雑になりすぎで汎化性能がでなくなることもある。
