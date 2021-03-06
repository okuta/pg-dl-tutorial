# 3. 目的関数を最適化することで，モデルを学習する (2)

この最適化問題を解くために，次のような戦略をとります。

1. 現在の位置 $x_t$ から目的関数の値が最も急激に下がりそうな方向を調べる

    * この方向を勾配と呼び，$-v_t$ と書きます。

2. その勾配にしたがって現在の位置から少し動かす: $x_{t+1} = x_t - \alpha_t v_t$

    * この時のステップ幅 $\alpha_t > 0$ を更新律と呼びます。

3. 1. 2.を関数の値が変わらなくなるまで繰り返す

このような最適化手法を勾配降下法と呼びます。

勾配降下法において，最も大変なのが勾配 $v_t$ の推定です。
実際のパターゴルフのような三次元の世界では，一番急激に下っている方向を探すのは簡単です。
一方，ディープラーニングの場合は一番急激に下がっている方向を探すために，誤差逆伝播法（back propagation）を利用し推定します。
誤差逆伝搬法の計算量は順計算の計算量とほぼ同じであり効率的に勾配を求めることができます。


## 誤差逆伝播法(*)

出力から入力に向かって，目的関数の出力についての勾配を伝播させていくことで効率的に勾配を求めることができます。
