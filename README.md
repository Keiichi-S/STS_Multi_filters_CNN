# STS_Multi_filters_CNN
このソースコードは,SemEval-2014のSemanticTextualSimilarityというタスクを想定して作成した物である。

## データセット
モデルの入力は"GoogleNews-vectors-negative300.bin.gz"という学習済みのWord2Vecを利用して単語を分散表現にした物である。
訓練データは、STS.input.OnWN.txt、STS.input.MSRvid.txt、STS.input.SMTeuroparl.txt、STS.input.tweet-news.txtの4つである。

## モデルの特徴
- サイズが3、5、7の3つのフィルターを並行して用いることで、多様な側面から文章の特徴を抽出
- 畳み込みを行う前にSelf-Attentionを計算することで、入力単語に対して重要度を計算
- 畳み込みとプーリング処理の後にGlobalAveragePoolingを利用することで文ベクトルを生成
- 残差接続を施すことで、情報が落ちてしまうことを防止
- 文章の類似度は、cos類似度を利用
- 3つの類似度の平均をとることで、アンサンブル学習の実現

## 精度
テストデータSTS.input.images.txtに対して0.81である。
