![comp](./data/info/readme/001.png)
# kaggle-Mechanisms-of-Action-MoA-Prediction
[Mechanisms of Action (MoA) Prediction](https://www.kaggle.com/c/lish-moa/overview) コンペのリポジトリ


## Basics
Mechanism of Action(MoA)とは、薬剤がその薬理学的効果を発揮するための特異的な生化学的相互作用を意味する。 ([参考](https://ja.wikipedia.org/wiki/作用機序))

### info
- [googledrive](https://drive.google.com/drive/u/1/folders/1JGawvjsXcoTEVL_VHkRvE1J7-UclvA7u)
- [issue board](https://github.com/fkubota/kaggle-Mechanisms-of-Action-MoA-Prediction/projects/1)

### Overview(DeepL)
MITとハーバード大学ブロード研究所、ハーバード大学イノベーション科学研究所（LISH）、NIH Common Funds Library of Integrated Network-Based Cellular Signatures（LINCS）内のプロジェクトであるコネクティビティマップは、MoA予測アルゴリズムの改善を通じて医薬品開発を前進させることを目的に、この課題を提示しています。

医薬品の作用機序（MoA）とは何か？また、なぜそれが重要なのでしょうか？

過去には、科学者たちは天然物から薬を導き出したり、伝統的な治療法に触発されたりしてきました。米国ではアセトアミノフェンとして知られるパラセタモールのような非常に一般的な医薬品は、その薬理作用を駆動する生物学的メカニズムが理解される何十年も前に臨床使用されていました。今日では、より強力な技術の出現により、創薬は過去のセレンディピタス的アプローチから、疾患の基礎となる生物学的メカニズムの理解に基づいた、よりターゲットを絞ったモデルへと変化している。この新しい枠組みでは、科学者たちは病気に関連するタンパク質ターゲットを特定し、そのタンパク質ターゲットを調節できる分子を開発しようとします。特定の分子の生物学的活性を説明するための略語として、科学者たちは作用機序（mechanical-of-action）または略してMoAと呼ばれるラベルを割り当てます。

新薬のMoAはどのようにして決定するのでしょうか？

1つのアプローチは、ヒト細胞のサンプルを薬剤で処理し、次に、遺伝子発現のライブラリや既知のMoAを持つ薬剤の細胞生存率パターンなど、大規模なゲノムデータベースの既知のパターンとの類似性を検索するアルゴリズムを用いて細胞応答を分析することです。

このコンペでは、遺伝子発現データと細胞生存能データを組み合わせたユニークなデータセットにアクセスすることができます。このデータは、100種類の細胞タイプのプール内の薬剤に対するヒト細胞の反応を同時に（同じサンプル内で）測定する新技術に基づいています（このようにして、ある薬剤に対してどの細胞タイプがより適しているかを事前に特定するという問題を解決します）。さらに、このデータセットに含まれる5,000以上の薬剤のMoAアノテーションにアクセスできます。

恒例のように、データセットはテストとトレーニングのサブセットに分割されています。したがって、トレーニングデータセットを使用して、テストセットの各ケースを1つ以上のMoAクラスとして自動的にラベル付けするアルゴリズムを開発することがあなたの課題です。薬物は複数のMoAアノテーションを持つことができるので、このタスクは正式にはマルチラベル分類問題であることに注意してください。

解の精度を評価するには？

MoAアノテーションに基づいて、各薬剤-MoAアノテーションのペアに適用される対数損失関数の平均値に基づいて、ソリューションの精度が評価されます。

成功すれば、あなたは、その細胞署名を与えられた化合物のMoAを予測するアルゴリズムの開発に貢献し、科学者が創薬プロセスを前進させるのに役立ちます。

### Data Description(DeepL)
このコンテストでは、遺伝子発現データや細胞生存率データなどの様々な入力を与えられた異なるサンプル（sig_id）の作用機序（MoA）応答の複数のターゲットを予測します。

2つの注意点があります。

トレーニングデータには、テストデータには含まれず、スコアリングには使用されないMoAラベルの追加（オプション）セットがあります。
再実行データセットは、パブリックテストで見られる例の約4倍の数を持っています。

train_features.csv - 訓練セットの特徴量．cp_type は化合物（cp_vehicle）または制御摂動（ctrl_vehicle）で処理されたサンプルを示し、制御摂動は MoA を持たない。cp_timeおよびcp_doseは、治療期間（24時間、48時間、72時間）および投与量（高値または低値）を示す。
train_targets_scored.csv - スコアされるバイナリMoAターゲット。
train_targets_nonscored.csv - 訓練データの追加の（オプションの）バイナリMoA反応。これらは予測もスコア化もされません．
test_features.csv - テストデータの特徴量．テストデータの各行のスコアされたMoAの確率を予測する必要があります．
sample_submission.csv - 正しい形式の提出ファイル．


### input

|filename|file size|shape|
|----|---|---|
|sample_submission.csv|3.2M|(3,982, 207)|
|test_features.csv|25M|(3,982, 876)|
|train_features.csv|150M|(23,814, 876)|
|train_targets_nonscored.csv|19M|(23,814, 403)|
|train_targets_scored.csv|9.7M|(23,814, 207)|

**train_fatures.cv**
- shape: (23814, 876)
- cpはcompoundの略っぽい

|columns|detail|
|---|---|
|sig_id|薬の種類|
|cp_type|化合物で処理されたのか、制御摂動で処理されたのかを示す。cp_vehicl or cp_ctrlの二値を取る。制御摂動(cp_ctrl)はMoAを持たない。|
|cp_time|処理時間。24, 48, 72の3値を取る。|
|cp_dose|投与量。D1, D2(high, low)の2種類。|
|g-[0, 771]|signify gene expression data. mRNAのデータ。|
|c-[0, 99]|signify cell viability data. 細胞の生存率を表す。|

## features
## Log
### 20201006
- join
- data download
- data size list


- nb001
    - inputデータのEDAを行った

### 20201007
- 今日はkaggle日記にinputを追加。
- この[EDA](https://www.kaggle.com/isaienkov/mechanisms-of-action-moa-prediction-eda)ノートブックを読んだ。

### 20201008
- 銀河さんのいつもの[イケイケEDA](https://www.kaggle.com/headsortails/explorations-of-action-moa-eda)みてた。
    - Treatment features

        <img src='./data/info/readme/002.png' width='500'>
    
    - Target
        - MoAが同時に活性になっている数

        <img src='./data/info/readme/003.png' width='500'>
        
    - 各クラスでアクティブになってる数(n_sample=23,814)
        - 最大800以上
        - 最小1

        <img src='./data/info/readme/004.png' width='500'>

### 20201010
#### チームマージした日！！
チーム名は、**May the CV be with you.** になった！

<img src='./data/info/readme/005.png' width='1000'>


### 20201011
- cool_rabbit さんからいろいろドメイン知識を学ばせてもらった。([slack](https://moagold.slack.com/archives/C01D1R2KCV6/p1602308954001100))
- cool_rabbitさんから教えてもらった[実験の論文](https://www.cell.com/cell/fulltext/S0092-8674(17)31309-0?_returnURL=https%3A%2F%2Flinkinghub.elsevier.com%2Fretrieve%2Fpii%2FS0092867417313090%3Fshowall%3Dtrue)
- cool_rabbitさんからホストがやりたいことを教えてもらった。おもったより簡単だった...

    ```
    ホストが開発した未来の薬剤候補(id)がたくさんあって、これらが既存の207種類の薬の中の何個の働きを持つかを知りたいわけです。
    ```
- cool_rabbitさんから得たとメイン知識をslideでまとめた
    - [googleslide](https://docs.google.com/presentation/d/1TyYxMozqOpxq0v212EIk8PLh53fdQ84AEM41otwAHvQ/edit#slide=id.g9c253d643f_0_348)
- ひらゆきさんとNicoNecoさんが参考にしている[公開ノートブック](https://www.kaggle.com/nicohrubec/pytorch-multilabel-neural-network)をベースにしよう