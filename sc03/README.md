# セクション3 最初の例題：学習から識別まで

## 資料
- scikit-learn　：　http://scikit-learn.org/stable/

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