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
