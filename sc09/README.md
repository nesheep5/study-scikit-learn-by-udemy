# セクション 9 学習サンプル数が多いとき

## LinearSVC
カーネルがリニアのSVMを実行する場合は、専用のクラスが用意されているのでそちらを使う方が高速。
-  sklearn.svm.LinearSVC
### ソルバの指定
ソルバはprimal,dualを選択することができる。dualは特徴量が多いときに有効。primalはサンプル数が多いときに有効。

## 確率勾配法（SGD）
LinearSVCよりも高速に識別することができる。ビッグデータを扱う場合に有利。  
SGDはランダム性があるため、サンプル数が少ない場合はロジスティック回帰やSVMを使ったほうがよい。  
