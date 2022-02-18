# analyze_tennis

スコアシートイメージ図を貼ります。
手書きです。

![1枚目](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1cc05170-24a9-4ea3-b77f-e860e0dc6973/IMG_3412.heic)

![2枚目](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/670a634f-7946-4591-94b7-fdad8a16db3d/IMG_3413.heic)

![球種など入力項目一覧](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f74e8eeb-bf88-4d4d-8b12-842a014086e5/IMG_3415.heic)


### **3行で**
自分の技術の何が強みで何が弱みか分からない人に
データと傾向を示して客観的に自分の能力を判断できるようにする
ソフトテニス分析サービスです

### **メインのターゲットユーザー**
・ソフトテニスの試合でスコアシートをつけている人
・練習量は多いのに技術に伸び悩んでいる人
・自分の強み、弱みを把握できていない人

スコアシートは以下のようなものです
![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9d0139d-a1d2-496e-96f0-d4040149869b/Untitled.png)

### **ユーザーが抱える課題**
・ソフトテニスの技術向上のために練習をしているが、伸び悩んでいる。
・紙の分析シートを使って試合のスコアをとっているが、なんとなくデータを取っているため上手く活用できていない。
・校内試合でダブルスをするときはプレーヤー4人に対して紙スコアシート1枚のため、全員が保管しようとするとコピーを取る必要があるため手間。
・1試合1試合のスコアは確認できるが、トータルのデータで傾向を見ることができないため、自分の強み、弱みを見つけにくい。
・自分の弱みを克服するための練習がわからない（そもそも弱みが何かわからない）。
・紙スコアシートをチーム全員で共有できないため、周りの意見を取り入れることができない。

### **解決方法**
・紙スコアシートのデータをグラフ化して、自分の強み・弱みが見えるようにする。
・グループ機能、コメント機能を作成し、メンバー全員でデータ確認しアドバイスし合えるようにする。

### **実装予定の機能（以下の例は実際のアプリの機能から一部省略しています）**
・データを取る
球種、コース、結果（スマッシュ、クロス、サイドアウトなど）

データをとる方法で迷っています。

○現状
プレーヤーの他にスコアシートをつける人がいて、その人がリアルタイムで書き込んでいる。

迷っている案↓
①上記紙スコアシートのようにリアルタイムで個人データを取りながらゲームを進行していく機能作成
各ポイントのデータをとる、同時にゲームのポイントも進行させる
→試合が終わりデータ送信
→各プレーヤーにデータが登録される
→試合終了後、各プレーヤーのデータをデータベースに保存
複数プレーヤーのデータを同時に保存できるのか？

個人データのみとりたい時（ゲームデータいらない時）には不便。

②今まで通り紙スコアシートは書いてもらう
紙スコアシートを見ながら各自がデータ入力。
機能としては簡単でこれなら実装のイメージがつく。
1枚のスコアシートを、共有しなければいけないので、入力が終わるのを待つ必要がある。

当初の考えでは、ゲーム全体のデータよりも、各自の強み・弱みを知ることだったので、各自のデータのみとれればよいと考えていた。
でもユーザーとしては、リアルタイムでゲームを記録しながらデータもとれる機能が欲しいはず。
⇨ゲームモード、フリーモードを作って、データの取り方を変えられるようにする。

- データをグラフ化（レーダーチャート 、傾向を見るための折れ線グラフ）

- ユーザー登録機能
・一人一人のデータを保存するために必要

- グループ機能
・グループ作成者がホストとなって、メンバーをグループに招待する。
・グループに所属してるユーザーのみ、グループ内のデータを見れるようにする。他のチームにデータを見られないように。
・メンバーのデータを確認して、お互いに検討できるようにする。
・個人個人の傾向だけでなく、チームの傾向も確認できると良い？

- コメント機能
・お互いに検討できるように

### **なぜこのサービスを作りたいのか？**

自分は高校・大学でソフトテニス部に所属して、上記の通り紙媒体のスコアシートを使用していたたが、改善したい点が2つある。

1. 自分の技術をグラフで見えるようにしたい、傾向から考察できるようにしたい
傾向は複数データを取り続けることで見えてくるものだが、この紙スコアシートではそれを見るのが困難だった。
プレーヤーに対してスコアシート1枚のため、1人で全て保管するわけにはいかない（大会でシングルスならば1人だが、校内試合ではシングルスでもプレーヤー2人）。
一人一人が傾向を確認できて、自分の強み・弱みがわかるようにしたい。
傾向がわかれば、どんな練習をすればいいか分かり、また日々の練習で強み・弱みを意識すると練習の質も変わるはず。
2. 全員で共有できるようにしたい
チーム全員に自分の傾向を見てもらうことで、色んな意見を取り入れることができ、一人では気づけないポイントが見つかる。意見を出し合うことで、チームの分析力が上がり、チーム全体のレベルアップにつながる。

### 類似サービス

↓類似サービスを紹介しているサイトがあった。
[https://minkara.carview.co.jp/userid/682401/blog/37244272/](https://minkara.carview.co.jp/userid/682401/blog/37244272/)

自分が作りたいサービスとは以下の点で異なります。

・取りたいデータが違う（上記のサイトはソフトテニスに特化していないため、若干ではあるが取りたいデータとは異なる）。
・折れ線グラフで傾向が見えるようにしたい。このショットの精度上がってきている、このミスが多くなってきているなどに気付けるようにするため。
・グループ機能を作成して、データ共有したい。

### **スケジュール**

README〜ER図作成：2/25 〆切
メイン機能実装：2/25 - 3/31
β版をRUNTEQ内リリース（MVP）：3/31〆切
本番リリース：4月末