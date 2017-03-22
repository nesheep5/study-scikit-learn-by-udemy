# セクション 6 テストデータの評価方法

## 2クラス問題のconfusion matrix
2クラス問題の認識率の内訳を調べたいときに使用する  
例：ガンなのに非ガンと推測 or 非ガンなのにガンと推測

以下の４つで表現する
- TP：True Positive 真陽性 (テスト:ガン 予測:ガン)
- TN：True Negative 真陰性 (テスト:非ガン 予測:非ガン)
- FP：False Positive 偽陽性 (テスト:非ガン 予測:ガン)
- FN：False Negative 偽陰性 (テスト:ガン 予測:非ガン)→これが多いとまずい

sklearnで用意されているクラス
- sklearn.metrics.accuracy_score
- sklearn.metrics.confusion_matrix

## classification_report
sklearn.metrics.classification_reportを使って、以下のレポートを出すことができる

### precision 適合度，精度
TP / (TP + FP) で表す。  

### recall 再現率
TP / (TP + FN) で表す。  
True positive rate (TPR)
2クラス問題のときは 0:sensitivity 感度 / 1:specificity 特異度 と表現されることもある。

### f1-score
各クラスでprecisionもrecallも良い数値を出しているかを表す指標。F値とも呼ばれる。  
 2 / (1/recall + 1/precision)で表す。

以下のようなクラスが用意されている
 - sklearn.metrics.f1_score
 - sklearn.metrics.fbeta_score

### 上記情報をまとめて取得
以下のクラスを使うとまとめて情報取得できる
 - sklearn.metrics.precision_recall_fscore_support

## 性能評価
- ROC (Receiver Operating Characteristic) : 縦軸にTrue Positive、横軸にFalse Positiveの割合を2次元プロットして点を線で連結した曲線
- AUC (Area Under the Curve) : ROC曲線の曲線よりしたの面積。分類器の精度評価に使う
