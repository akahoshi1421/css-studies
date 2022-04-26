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

## @import
ほかのファイルを読み込む

    /*_mixin.scssとした場合
    (アンダーバーに注意)*/

    @import mixin;

    //生のCSSの読み込みはurl()を使う
    @import url("desktop.css") screen and (min-width: 601px);

    //これは「「「「できない」」」」ので注意！！
    //@import "desctop" screen and (min-width: 601px);

    //SCSSから読みたい場合こうする
    @media screen and(min-width: 601px) {
       // @import "desktop.scss";
    }

    /*この書き方がおすすめ
    desktopの方が書かないといけないスタイルが多いのでモバイルベースでやった方がいい*/
    //@import "mobile.scss";

    @media screen and (min-width: 601px) {
       // @import "desktop.scss";
    }


## @each
連想配列風にした変数を取り出せる

    $pattern: (
    "up": translateY(6px),
    "down": translateY(-6px),
    "left": translateX(40px),
    "right": translateX(-40px),
    );

    @each $key,$value in $pattern {
        //keyが左、valueが内容
        .appear.#{$key}{
            & .item{
                transform: $value;
            }
        }
    }

## @extend

    .aaa{
        background-color: black;
        color: white:
        font-size: 2vh;
    }

    .bbb{
        border: 1px solid black;
        @extend .aaa;
        //これによって.aaaに書かれている内容を.bbbに読み込める
    }

## セレクタ(この辺はCSSだけど)

    & > .aaa{
        /*子要素のみ変更(孫要素は変わらないので注意)*/
    }