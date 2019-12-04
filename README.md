# STS_Multi_filters_CNN

このソースコードは,SemEval-2014のSemanticTextualSimilarityというタスクを想定して作成した物である。

モデルの入力は"GoogleNews-vectors-negative300.bin.gz"という学習済みのWord2Vecを利用して単語を分散表現にした物である。
訓練データは、STS.input.OnWN.txt、STS.input.MSRvid.txt、STS.input.SMTeuroparl.txt、STS.input.tweet-news.txtの4つである。

特徴は、フィルターサイズが3、5、7の3つのフィルターを並行して利用しているところで、これにより多様な側面から文章の特徴を得ている。
文ベクトルの作り方は、畳み込みとプーリング処理の後にGlobalAveragePoolingを利用することで作成している。
また、残差接続を施すことで、情報が落ちてしまうことを防いでいる。
文章の類似度は、cos類似度を利用して求め、3つの類似度の平均をとることで、アンサンブル学習を実現している。

精度は、テストデータSTS.input.images.txtに対して0.81である。
