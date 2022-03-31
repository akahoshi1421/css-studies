# Sassの記法
## 変数
    $変数名: aaaa;
    /*こんな感じで定義できる*/


## ネスト
    .btn{
        /*こんな感じでhoverをつける際は&:hoverをつける*/
        &:hover{
            background-color: $cBlack;
            color: $cWhite;
        }
    }

&をつけることで半角スペースがあかなくなる(.btn:hover)

    .aaa{
        .bbb{
            color: white;
        }
    }

これだと.aaa .bbbになる

## @mixin
関数でやりたいことをまとめられる

    @mixin animation($name, $duration: 1s){
        animation: {
            name: $name;
            duration: $duration;
        }
    }
↑引数に$duration: 1sと書くことでデフォルト値をかける
↑またanimation:{name:}とかで
animation-nameとかわざわざ書かないで済む

呼び出し側

    .rect {
        @include animation(
            $name: sk-bouncedelay
        );
    }

## @for
1~100まで

    @for $i from 1 through 100 {
      
    }

1~99まで

    @for $i from 1 to 100 {
      
    }

中身

    @for $i from 1 through 2 {
      &:nth-child(#{$i}){
        //セレクタに変数を埋め込みたい場合、#{$変数}と書く
        animation-delay: -0.32s / $i;
      }
    }

文字列に変数を埋め込む場合

    backgroud-image: url("/image#{$i}.png");

## セレクタ(この辺はCSSだけど)

    & > .aaa{
        /*子要素のみ変更(孫要素は変わらないので注意)*/
    }