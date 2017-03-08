# セクション４　学習データとテストデータの準備

## 学習データのサンプリング
手持ちのデータを学習データとテストデータに分ける  
もし全てのデータで学習し、全てのデータでテストしたら過学習になってしまう  
###手法の種類
#### Hold-Out
手持ちのデータをランダムに分ける方法
#### Cross-Validation(交差確認)
手持ちデータをいくつかのグループに分け、順番に学習データとして使用する。
10グループに分ける場合は 10-fold-CV などと呼ぶ。  
####Leave-One-Out(一つ抜き法)
手持ちのデータの１つをテストデータに、それ以外を学習データにする。テストデータを一つずつずらして学習を繰り返す。  
手持ちのデータが少ない時に有効。
####Leave-One-Group-Out
手持ちデータがあるルールでグルーピングされているような場合(患者A,B,Cなど)グループの１つをテストデータとして利用する。

###Stratified(層化)
手持ちデータのクラス比率を保ったまま、学習データを作成する必要がある。

----

## sckit-learnに用意されているオブジェクト
### ShuffleSplit
- sklearn.model_selection.ShuffleSplit : ランダムなデータ抽出を行う
- sklearn.model_selection.StratifiedShuffleSplit : クラスの比率を保ったままランダムなデータ抽出を行う

###Cross Validation

sklearn.model_selection.KFold
```python
ss = KFold(n_splits=10, shuffle=True) # 10Fold-CV
```

クラスの比率を保ったままCross Validation  
sklearn.model_selection.StratifiedKFold

K分ループを回す関数が既に用意されている  
sklearn.model_selection.cross_val_score
```python
ave_score = cross_val_score(clf, X, y, cv=10) # StratifiedKFold
```
は下記と一緒
```python
from sklearn.model_selection import StratifiedKFold
ss = StratifiedKFold(n_splits=10, shuffle=True)

for train_index, test_index in ss.split(X, y):
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]
    print(np.unique(y_train, return_counts=True)[1] / y_train.size, y_train.size,
          np.unique(y_test,  return_counts=True)[1] / y_test.size,  y_test.size)
```
