# flexディスプレイ

## justify-content
横方向
* center etc..
* space-between
(端の要素は画面端にいき、あとは中央ぞろえ)
* space-around
(ウィンドウからみていい感覚での中央ぞろえ)

## align-items
縦方向
* center etc..

## flex-grow
flexの伸びを選択できる
例)全要素にflex-grow: 1
→すべての要素が1:1:1とかになる
2番目だけflex-grow: 2
→1:2:1になる

## flex-basis
flexの伸びを具体的に選択
1要素だけflex-basis: 300px
→300pxだけその要素が確保してから残りの要素が1:1とかで決める
    →全部これがついているとうまくいかないので妥協しあう

## flex-shrink
例えば全部にflex-basisを選択したときどうしてもこの要素だけ...っときに使う
→0にするとうまくできる
→その場合じゃなくても伸びを決めたいときとかにも使う

## flex-wrap
flex-basisで300pxとかを指定して足りないなってなったときに改行してくれる

## flex-direction: row-reverse;
反転する