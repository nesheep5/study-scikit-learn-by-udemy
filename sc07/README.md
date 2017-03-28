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
- sklearn.linear_model.Perceptron

### 学習則
### 損失関数
