# セクション 6 テストデータの評価方法

## 2クラス問題のconfusion matrix
2クラス問題の認識率の内訳を調べたいときに使用する  
例：ガンなのに非ガンと推測 or 非ガンなのにガンと推測（ガンなのに非ガンと推測するのはまずい）
- sklearn.metrics.accuracy_score
- sklearn.metrics.confusion_matrix
