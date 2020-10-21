![comp](./data/info/readme/001.png)
# kaggle-Mechanisms-of-Action-MoA-Prediction
[Mechanisms of Action (MoA) Prediction](https://www.kaggle.com/c/lish-moa/overview) コンペのリポジトリ


## Basics
Mechanism of Action(MoA)とは、薬剤がその薬理学的効果を発揮するための特異的な生化学的相互作用を意味する。 ([参考](https://ja.wikipedia.org/wiki/作用機序))

### info
- [googledrive](https://drive.google.com/drive/u/1/folders/1JGawvjsXcoTEVL_VHkRvE1J7-UclvA7u)
- [issue board](https://github.com/fkubota/kaggle-Mechanisms-of-Action-MoA-Prediction/projects/1)
- Important person

|name|detail|
|---|---|
|[mrbhbs](https://www.kaggle.com/mrbhbs/discussion?sortBy=latestPost&group=commentsAndTopics&page=1&pageSize=20)|ホスト。ドメイン知識に関するディスカッションのコメントによく現れる。|
|[Michael Maguire](https://www.kaggle.com/thawatt/discussion?sortBy=latestPost&group=commentsAndTopics&page=1&pageSize=20)|ホストに良い質問ぶつけてくれてるマスター。|

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

|filename|file size|shape|comment|
|----|---|---|---|
|sample_submission.csv|3.2M|(3,982, 207)|---|
|test_features.csv|25M|(3,982, 876)|このデータセットはpublicデータセットと完全に等しい。privateはpublicの4倍のサイズ。|
|train_features.csv|150M|(23,814, 876)|---|
|train_targets_nonscored.csv|19M|(23,814, 403)|---|
|train_targets_scored.csv|9.7M|(23,814, 207)|---|

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

### 20201012
- ベースラインの基礎としたい[公開ノートブック](https://www.kaggle.com/nicohrubec/pytorch-multilabel-neural-network/data?select=iterative-stratification-master)を見てた。
    - かなりシンプルで勉強しやすい。

- メンバーとpublicとprivateについて議論した。以下に[マインドマップ](https://drive.mindmup.com/map/1VMY-xOHTmjxZNqZdbZeo1aQIs_2-DPcL)でまとめた。
    - localのtest = publicのtest っぽいな...。本当か？

    <img src='./data/info/readme/006.png' width='1000'>

- TASSANとにこ猫さんと議論した。nonscoredを使うときは、以下のようにすべきという見解になった。

    <img src='./data/info/readme/007.png' width='500'>

### 20201013
- ひらさんから教えてもらったMultilabelStratifiedKFoldがoverfitしやすいという[ディスカッション](https://www.kaggle.com/c/lish-moa/discussion/181340)

- domain知識溜まりそうな[discussion](https://www.kaggle.com/c/lish-moa/discussion/184005)

    - PGE2とLTB4は分子(targetのどれか)で、CREBがg-xxxのどれかに相当する。
    - ATPからCREBまで続く回路がある
    - CREBまでいくとある遺伝子が発現する
    - 薬剤の投与で、この回路そ促進または、阻害することができる
    - PGE2がEP2に反応？すると、CREBの遺伝子発現が促進される
    - 逆にLTB4がBLT1に反応すると回路を阻害するため遺伝子発現は抑制される
    - つまり、CREBなどの遺伝子発現を観測することで、PGE2やLTB4のどれが働いたのかが関節的にわかる。

    <img src='./data/info/readme/008.png' width='500'>

    - cp_timeに関して
        - 72時間経過すると、薬剤はその効果を失う可能性がある。つまり、コントロールと区別がつかない場合がある。
    - 手元にあるtestデータは、publicのデータセットに等しい。
        - privateのデータセットは完全に未知。

- dataに施した前処理は、quantile normalizationだけではないらしい。([discussion](https://www.kaggle.com/c/lish-moa/discussion/184005#1034211))

- cool_rabbitさんに質問(コントロール群について)
    - (fkubota)ctl_vehicleは薬剤を投与していないという認識なのですが正しいですか？
    - (cool_rabbit)DMSOという薬液(濃度が薄ければ細胞には無害とされている)を投与していると思われます。
    - (fkubota)DMSOは6パターン(time3パターン x dose2パターン)あればいいのでは?
    - (cool_rabbit)理由はおそらく2つあって、
        - 同じ量と時間でも実験するたびにばらつきがあるので複数回する必要がある
        - 本物の薬剤候補を使って実験する時は、同時に同じプレートにコントロールを置く必要がある
        後者に関して、例えば晴天の日にtreatment群をやって、雨天の日にcontrol群をしてしまうと、未知の天気の影響が実験に出るかもしれないですよね。なので必ず同じ日に同じプレート内でコントロールを置く必要があります。ただしコントロールの数を薬剤と同じ数ほどは用意しなくてもいいので、例えば薬剤10種類とDMSO1つを同じプレート内の異なる11個の穴で同時に実験しているイメージです。

### 20201014
- [このディスカッション](https://www.kaggle.com/c/lish-moa/discussion/184005#1034211)で、quantile normalizationについて言及している
    - qn されていれば、ユニークな値になるはす。しかしなっていない。
    - ホストはqnしていると[コメント](https://www.kaggle.com/c/lish-moa/discussion/180390#1000307)している。
- sklearnのメトリックlog_lossはある(targetの)カラム全てに0が入っているとエラーが出る仕様になっている。
    - 以下のように自分で定義すればよさそう。
        ```python
        def log_loss_metric(y_true, y_pred):
            loss = - np.mean(np.mean(y_true * np.log(y_pred) + (1 - y_true) * np.log(1 - y_pred), axis = 1))
            return loss
        ```
    
- ぼーっとEDAしてた。
    - 最大値最小値を-10~10に正規化してるけど、min_max_scalerじゃなくて、サチュレイトさせてるっぽいんだよなー。  

    <img src='./data/info/readme/009.png' width='500'>  

    こんなアイデアおもしろいのでは？  
    <img src='./data/info/readme/010.jpg' width='300'>  

### 20201015
- cool_rabbitさんのアイデア(leak を避ける方法)
    - target の総数でグループ分けする

- 上の手法だと、たかだか12種類程度にしかわけることができないらしい。
    - しかもimbalanced...

- ちょっと問題整理してみよう。
    - 以下の図はすべて違う薬剤だが、sumだと縮退してしまう。見た目でわかるということはユニークな値にできるはず...

    <img src='./data/info/readme/014.jpg' width='300'>  


- 打開策思いついた！！

    |1|2|3|
    |---|---|---|
    | <img src='./data/info/readme/011.png' width='400'>  | <img src='./data/info/readme/012.png' width='400'>  | <img src='./data/info/readme/013.png' width='400'>  |

- nb003
    - 上のアイデアを参考にノートブックを作成。
    - チームメイトにも展開した。
    - 特に間違ってなさそう。
    - グループは696個形成された。ただし、1グループ1sig_idというのも存在している。もう少しEDAしてみたほうがいいかもしれない。
    - analysis
        - trt_cpのみに絞ってgroupカラムでvalue_countsを行った。(group=1がall_target=0となる)
            - 1はやはり多い。

            <img src='./data/info/readme/015.png' width='300'>  

- TASSANの意見。たしかにそうだな...

    ```
    あるtargetが1つのfoldに集約すると以下のような問題点が起きると思います。
    ２fold分割、target1がfold1のみに存在し、testを推論する状況を考えます。
    １．fold1がtrain, fold2がvalidのとき、testのtarget1を予測する
    →問題なし(この予測とtest1とする)
    ２．fold2がtrain, fold1がvalidのとき、testのtarget1を予測する
    →fold2(trainデータ)にtarget1が存在しないのでこの予測にほとんど意味がなく、
    予測値がほぼ0になると思われる(この予測をtest2とする)
    このときに一般的にはtest1とtest2を行(sig_id)ごとに平均したものをsubmitに使うと思うのですが、
    そうすると予測値がほぼ0のものが必然的に混ざってしまい、あまりよろしくない予測になってしまうのでは？という懸念があります。
    極端の場合、１でtestのtarget1をほぼ間違いなく当てられるようなモデルを作ったとしても
    submitの際に予測値がほぼ0になってしまう２が混ざってしまうので、target1の予測精度が悪化するということが考えられます。
    (この場合の対処は簡単で、testのtarget1の予測には１で作ったモデルの推論のみを使う事が考えられます)
    以上が気を使ったほうが良いと言った具体的な内容です(完全に説明不足でした
    ```

- ホスト側の視点にたって考えてみた。
    ```
    ちょっとホスト側の気持ちになって考えてみたのですが、
    ABC=100
    ABC=010
    ABC=110
    のようなパターンがtrainには入っており、

    trainにはないパターン
    ABC=001
    がtestにある場合は考えられますよね？

    206のターゲットカラムの内、2つが1になる組み合わせ206C2=21115パターンあり、
    おそらくtrainで全ては網羅していないと思っています。(ましてや、3つが1になる組み合わせとなると...)
    それに同じ薬剤効果しかみつけられないモデルというのはホストは望んでいないのではないでしょうか。

    我々はむしろ、
    ABC=100
    ABC=010
    を学習して
    ABC=110
    を予想できるようなモデルをつくらなければいけないのではないかと考えました。
    参考までに。
    ```
    - TASSANからは同意をもらえた:)

- 現状の整理
    ```
    いろいろごちゃごちゃしてきたので、一旦整理させてください。
    僕がコメントしたこちらの思想のもとであれば、
    今の所、以下の課題があるにせよ696グループ分けが最善っぽい？という認識でいいでしょうか？
    
    課題
    - all_target = 0 のサンプルが極端に多い([https://moagold.slack.com/archives/C01D1R2KCV6/p1602818235291300?thread_ts=1602812717.288100&cid=C01D1R2KCV6)
    - 同じグループに異なる薬剤が入っている(できればなんとかして分けたいが、リークのリスクがある)
    - grupKFoldした時に、trainとvalidに同じ薬剤効果パターンが現れない(しかし、上記思想のもとでは問題にしなくてもいいかもしれない)
    - あるターゲットを見たときに、そのターゲットしか1にならない(他の205ターゲットは0)場合が極端に多いときに、
      fold間でそのターゲットの極端な不均衡が生まれてしまう。(TASSANの意見を追加)

    メリット
    - リークの問題からは開放されたはず。
    - リークの問題から開放される手法の中では今の所最も微細な構造をもつグループである。

    僕は、この認識です。
    ただ、思想の部分はまだ議論の余地はあるとは思っています。
    同意でも反論でもいいのでみなさんと認識を合わせたいです。
    よろしくおねがいします。
    ```

### 20201017
- cool_rabbitさんからのお告げ
    ```
    以下はそのGroup内の一部のsig_idで細胞殺傷能力が高い(cで-10近くの値)ものです。
    ・G1: MoAなし
    ・G10: dna_inhibitor
    ・G23: pdgfr_inhibitor
    ・G33: pi3k_inhibitor
    ・G34: sodium_channel_inhibitor
    ・G42: topoisomerase_inhibitor
    ・G124: serine_threonine_kinase_inhibitor
    ・G169: protein_synthesis_inhibitor
    ・G173: alk_inhibitor
    ・G189: atpase_inhibitor
    ・G201: selective_estrogen_receptormodulator(serm)
    ・G225: topoisomerase_inhibitor+rna_synthesis_inhibitor
    ・G328: proteasome_inhibitor
    ・G364: aurora_kinase_inhibitor+mek_inhibitor
    ・G374: exportin_antagonist
    ・G377: estrogen_receptor_antagonist
    ・G444: stat_inhibitor
    ・G451: apoptosis_inhibitor
    ・G471: flt3_inhibitor+jak_inhibitor
    ・G513: cyclooxygenase_inhibitor+lipoxygenase_inhibitor+nfkb_inhibitor+histone_acetyltransferase_inhibitor
    ・G584: apoptosis_stimulant+bcl_inhibitor+ikk_inhibitor+nfkb_inhibitor+nitric_oxide_production_inhibitor+nrf2_activator+ppar_receptor_agonist+glutathionereductase(nadph)_activators+heme_oxygenase_activators+reducing_agent
    ・G634: na_k-atpase_inhibitor
    ・G637: flt3_inhibitor+kit_inhibitor+pdgfr_inhibitor+vegfr_inhibitor+ret_inhibitor
    逆にこれら以外のGroupは細胞殺傷能力は弱〜中程度でした。
    ```

- ドメイン知識を得るのに重要な[discussion](https://www.kaggle.com/c/lish-moa/discussion/191487)
    - めっちゃ質問しまくってる。


### 20201018
- 鬼滅の刃 10冊読んでしまった。
- 面白かったから良しとする。


### 20201019
- nb002
    - とりあえず5-foldでコード書いた。
    - ただ、KFoldで5分割しただけなので、薬剤リークが存在する。
    - result
        - cv: 0.015140
        - loss

        <img src='./data/info/readme/016.png' width='400'>  

### 20201020
- nb002の後半で、log_lossの挙動見てたけど、結構えぐい。後処理考えないとなー。

    <img src='./data/info/readme/017.png' width='400'>  

- kaggle001
    - nb002のモデルを使う
    - result
        - cv:  0.015140
        - sub: 0.01910

- nb004
    - targetの情報を用いてgroupを作成する
    - nb003では、696個にグルーピングした。
    - all_target = 0 のグループがかなり多いのでそれを細かく分割しようと思う。
    - get_696_strategy_fold(group, n_splits) という関数を作成した
    - get_696_strategy_fold
        - group_0とgroup_not0分ける
        - gourp_0を5fold, group_not0をgroup5foldする
        - fold情報を合体させる


- nb005
    - nb004で作成した、get_696_strategy_foldを使用した
    - result
        - n_splits = 5
        - cv: 0.024645

### 20201021
- kagglenb002
        - nb005で作成したモデルを使用
        - result
            - cv:  0.024645
            - sub: 0.02057

- nb006
    - nb005のcvが良くなかったので、その解析を行なう
    - おそらく、foldごとにtargetの分布差が生じているものだと思われる。
    - それを一定にするような方法を考える。
    
    - 任意のtargetが1になる回数を各fold毎にプロット

        <img src='./data/info/readme/018.png' width='1000'>  

    - 上記の図をbinary化

        <img src='./data/info/readme/019.png' width='1000'>  

    - 各targetがgroupに出現する回数を数えた
        - 悲報: 206のターゲットの内、88はある一つのグループに属していることがわかった。

