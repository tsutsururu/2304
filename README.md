# 2304

# 0404

# 088D  Grid Repainting   diff 999

解答遷移  AC

計 18:45

➀ 思考

最短経路を成さない白マス以外の白マスすべてを黒く塗るのが最適。したがって、bfs で最短経路 X を調べ、HW - (X+1+ 黒マスの個数) を求めればよい

# 0405

# ☆ HHKB2020E  Lamps  diff 1399

降参

➀ 思考

そのマスを照らせるマスの個数 x を求めておくと、Σ (2^x-1) * (2^(K-x)) で計上できる。⇒ TLE/ 勘違いしていたが、そのマスを照らせるマスを計上するために素直に直進する処理を行うことは O(HW * (H+W)) で間に合わない。

工夫として二次元 imos 法で計上しようとしたが、全然うまくいかず降参

➁ 解法

1, 区間計上

まず、この問題は二次元 imos で解決しやすい区間問題ではない。二次元 imos は一次元 imos の純粋な拡張ではないからである。

129D Lamps のようにそのマスから照らせるマスを、近接 # マスを二分探索で調べて計上する処理が区間の数え上げには簡単だと思われる。

もしくは、そのマスから左に何マス照らせるかを調べたテーブル、右に何マス照らせるかを調べたテーブル、下、上、それぞれを　O(HW) で作成し、L+R+D+U-1 で計上するのも良い。こちらの方が二分探索より高速

2, 個数計上

(pow(2,count,MOD) - 1) × pow(2,K-count,MOD) で計上する場合、pow処理で log2000 = 10 要してしまうと、掛け算を O(n) で行った場合、全体で O(10n × HW) となり、定数倍が重くてTLE してしまう。

この時、DP の要領で pow テーブルを作成しておけば 2^X を O(1) で求めることが可能になる。

③ 感想

pow で計算量を削減する問題に初めてであった。この問題の肝である個数数え上げは 10分たらずにできたのに、尺取り法にこだわり過ぎて区間計上できなかった点、本質ではない pow で TLE 悩まされる点でとても気持ちが悪い思いをした。




# 0406

# Walk and Teleport  diff  1060

解答遷移 AC

計 04:18

➀ 思考

町は昇順に訪問できるので、単純に (X[i] - X[i-1]) * A と B を比べ続ければよい。











