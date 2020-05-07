# Let's Try！ Ruby on Rails :bowtie:
## Ruby on Rails とは？
プログラミング言語の**Ruby**を使用したオープンソースのWebアプリケーションフレームワークのひとつです。   
・フレームワークとはWebアプリケーションを開発する際に、簡単に行えるようにする骨組みのことです。  

**Ruby on Railsを使用するメリット**  
**①初心者でも開発しやすい**  
上記でも述べた通り、Ruby on Railsではプログラミング言語のRubyを使用します。プログラミング言語の中でもシンプルで書きやすいものとなっており、開発方法について日本語で解説しているものも多く、
それらを参照しながら進めやすく、初心者にも取り組みやすいです。  
**②素早く開発を進めることができる**  
Ruby on Railsでは、書き方に細かくルールが定められているため、そのルールに沿って行くことでスムーズにアプリケーションが開発できます。

### Ruby on Rails の基本理念
**Don’t Repeat Yourself(DRY)** *同じことを繰り返すな*  
これは同じことを繰り返さないで行きましょうという理念です。同じコードを繰り返し書くことを避けることにより、  
コードが保守しやすくなり、かつ簡単に拡張できるようになります。また何よりもバグを減らすことができます。  
**Convention Over Configuration(CoC)** *設定より規約が優先される*  
設定よりも規約が優先されるという考え方です。  
他のフレームワークでは、設定をその都度書いていくことによりソースコードが大量に必要となってしまう傾向があります。
Ruby on Railsでは、Webアプリケーションの各種設定についても従来の経験や慣習を元に、それらのデフォルトが定められています。
それにより複数で開発をする際にも、それぞれで共通の設定を使用することにより、開発工数の削減を実現できます。

参考サイト　[Railsガイド](https://railsguides.jp/)


## なぜこのテキストに取り組むのか？
皆さんはこれから実際にRuby on Railsを取り組んでいきます。  
Ruby on Railsを使用して具体的にどのようなものが作れるのか、まずは体感してみましょう。  
今回は「TweetMemory」というTwitterのようなSNSサイトを作成していきます。  

### 実際にRuby on Railsを使って目標物を作ってみましょう
#### ①このテキストによって完成するものを確認していきましょう
今回はこのようなWebサービスのトップページを作っていきます。   
![ws1-a](https://user-images.githubusercontent.com/64009174/80331023-e1486c00-8881-11ea-9aad-7e8a4d9b7e11.png)


#### ②実際にトップページを作成してみましょう
1. まずは今回作成するアプリケーションの準備をしましょう！  
   1. アプリケーションのためのフォルダを準備しましょう。  
    フォルダを作成する際は以下のコマンドで実行できます。  
    __rails new アプリケーション名__  
    今回は「TweetMemory」という名前で作成しますので、ターミナルで`rails new tweet_memory`と入力します。  
    `rails new`コマンドを実行すると、フォルダの中に今回作成していくアプリケーションに必要な複数のフォルダとファイルが自動で作成されます。  
    同時にGemfileというファイルで指定されているgemファイルがbundle installコマンドによってインストールされます。    　
    ☆フォルダの中身は `rails new -h` というコマンド入力で確認することができます。  
     フォルダ内部に作成される内容物については[Railsガイド](https://railsguides.jp/) の【Railsをはじめよう】をご覧ください。  
   1. コントローラを作成して、トップページを自動生成してみましょう。  
      コントローラーとトップページは`rails generate controller home top`で作成することが出来ます。    
      ☆このコマンドは`rails g controller home top`と省略することも可能です。
   1. 出来上がったトップページを確認してみましょう。  
      トップページを確認するためにはサーバーを起動する必要があります。  
      サーバを起動する際は、`rails server`とコマンド入力をすると実行できます。  
      ☆このコマンドは`railss s`と記述することもできます。  
      このコマンドを実行することで、新しいアプリケーションを作成後すぐに起動することが出来ます。  
      実行したら実際に[http://localhost:3000](http://localhost:3000) にアクセスしてみましょう。  
      作成したトップページが確認できます。  
      作成したトップページを確認する際は、localhost:3000/home/top にアクセスします。  
            
1. 表示される仕組みを知っておきましょう！  
   1. ビューについて  
   **ビュー**とは表示されるページの外見を作るためのHTMLファイルのことです。  
   `rails generate controller home top`を実行するとviewsフォルダの中に”homeフォルダ”が作成され、その中に”top.html.erb”というファイルが作成されます。  
     ☆「.erb」とは**Embedded RuBy**の略です。任意の場所でrubyのコードを埋め込んで使用することが出来ます。　　 
     まずはこの"top.html.erb"の中身を下記のように編集してみましょう。   
     `<h1> 今日の思い出を残そう。</h1> `     
 　　` <p>まずは今の気持ちから</p>　`     
     
       先ほど確認したトップページを再読み込みし、以下のように変更ができていれば成功です。  
     ![ws1-c](https://user-images.githubusercontent.com/64009174/81255018-8bd14380-9067-11ea-9747-14d0c5cf071c.png)　　

   1. コントローラについて  
   **コントローラ**はビューに表示する情報を変更することが出来ます。Railsを使用してページを表示するときにはこのコントローラを経由し、ビューをブラウザに表示させています。  
コントローラファイルの中身を確認する際は`rails generate controller home top`を実行した際に、自動作成されたcontrollersフォルダの中に”home_controller.rb”というファイルで見ることが出来ます。またこの中には”top メソッド”が追加されています。  
コントローラ内のメソッドのことを**アクション**と呼び、コントローラと同名のviewフォルダからアクションと同名のファイルをブラウザに返す役割を持ちます。

   1. ルーティングについて  
   **ルーティング**とは、ユーザーがアクセスしたＵＲＬをもとに**何を表示させるか？を仕分け**しています。　　
       ルーティングは、configフォルダの"routes.rb"というファイルに`get "表示するURL" => "コントローラー名#アクション名"`と記述されます。  
       今作成しているものは`get "home/top" => "home#top"`と書かれています。  
       この`get "home/top" => "home#top"`を`get "/" => "home#top"`へ変更してみましょう。  
       今まで”localhost:3000/home/top”にアクセスしていたものが、”localhost:3000/”でアクセスすることが出来るようになります。
     
     ![brc](https://user-images.githubusercontent.com/64009174/81259264-8fb69300-9072-11ea-9ffd-4223fc24f3fd.png)  
      
       ☆コントローラで値を定義していなかったり、ルーティングに記述していないURLにアクセスするとエラーになります。  
        Railsで実行したことがうまくいかない場合は何のファイルのどこにエラーが出ているかを丁寧に教えてくれます。
 
1. 実際にページを整えていきましょう！  
   1. 画像を準備しましょう  
    画像は"app/public"フォルダに格納しておくと、`<img src="/画像名" >`・`background-image: url("/画像名");`と画像名を記述するだけで、簡単に画像を呼び出せるようになります。 　　
    このとき画像名の前にある **/** を忘れると表示されないので気を付けましょう！  
    今回は下記の画像"top.png"を背景画像として使用します。  
    ![ws1-b](https://user-images.githubusercontent.com/64009174/81270429-b3370900-9085-11ea-8e08-599e08648fb4.png)  
    
   1. CSSを編集しよう  
      `rails generate controller home top`を実行した際、”app/assets/stylesheets”フォルダが作成されCSSファイルも同時に自動作成されます。
       Railsを活用すると、このstylesheetsフォルダの中に保存されているCSSファイルにコードを記述すると、すべてのビューにCSSが適用できます。 
        実際に ”app/assets/stylesheets”に入っている"home.css"に下記コードを貼り付けてみてください。  
        
<details>
<summary>home.cssに記述するコード</summary>

```
/*　---------------ここから---------------　*/ 
/* reset ================================ */
* {
  box-sizing: border-box;
}

html {
  font: 100%/1.5 'Avenir Next', 'Hiragino Sans', sans-serif;
  line-height: 1.7;
  letter-spacing: 1px;
}

ul, li {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

a {
  text-decoration: none;
  color: #2d3133;
  font-size: 14px;
}

h1, h2, h3, h4, h5, h6, p {
  margin: 0;
}

input {
  background-color: transparent;
  outline-width: 0;
}

form input[type="submit"] {
  border: none;
  cursor: pointer;
}

/* 共通レイアウト ================================ */
body {
  color: #2d3133;
  background-color: #3ecdc6;
  margin: 0;
  min-height: 1vh;
}

.main {
  position: absolute;
  top: 64px;
  width: 100%;
  height: auto;
  min-height: 100%;
  background-color: #f5f8fa;
}

.container {
  max-width: 600px;
  margin: 60px auto;
  padding-left: 15px;
  padding-right: 15px;
  clear: both;
}

/* ヘッダー ================================ */
header {
  height: 64px;
  position: absolute;
  z-index: 1;
  width: 100%;
}

.header-logo {
  float: left;
  padding-left: 20px;
  color: white;
  font-size: 22px;
  line-height: 64px;
}

.header-logo a{
  color: white;
  font-size: 22px;
}

.header-menus {
  float: right;
  padding-right: 20px;
}

.header-menus li {
  float: left;
  line-height: 64px;
  font-size: 13px;
  color: white;
  padding-left: 15px;
}

.header-menus a {
  float: left;
  font-size: 13px;
  color: white;
}

.header-menus .fa {
  padding-right: 5px;
}

.header-menus input[type="submit"] {
  padding: 0 20px;
  float: left;
  line-height: 64px;
  color: white;
  margin: 0;
  font-size: 13px;
}

/* top ================================ */
.top-main {
  padding: 200px 0 100px;
  text-align: center;
  position: absolute;
  top: 0;
  width: 100%;
  height: auto;
  min-height: 100%;
  color: white;
  background-color: #3ecdc6;
  background-repeat: no-repeat;
  background-position: center 50%;
  background-size: cover;
  background-image: url("/top.png");
  
}

.top-message {
  position: relative;
}

.top-main h2 {
  font-size: 70px;
  font-weight: 500;
  line-height: 1.3;
  -webkit-font-smoothing: antialiased;
  margin-bottom: 20px;
}

.top-main p {
  font-size: 24px;
}

/* about ================================ */
.about-main {
  padding: 180px 8% 0;
  color: white;
}

.about-main h2 {
  font-size: 64px;
  font-weight: 500;
  line-height: 1.4;
}

.about-main p {
  font-weight: 200;
  font-size: 20px;
}

.about-img {
  width: 84%;
}

/* フォーム================================ */
.form {
  max-width: 600px;
  margin: 0 auto;
  background-color: white;
  box-shadow: 0 2px 6px #c1ced7;
}

.form-heading {
  font-weight: 300;
  margin: 60px 0 20px;
  font-size: 48px;
  color: #bcc8d4;
}

.form-body {
  padding: 30px;
}

.form-error {
  color: #ff4d75;
}

.form input {
  width: 100%;
  border: 1px solid #d8dadf;
  padding: 10px;
  color: #57575f;
  font-size: 16px;
  letter-spacing: 2px;
  border-radius: 2px;
}

.form textarea {
  width: 100%;
  min-height: 110px;
  font-size: 16px;
  letter-spacing: 2px;
}

.form input[type="submit"] {
  background-color: #3ecdc6;
  color: white;
  cursor: pointer;
  font-weight: 300;
  width: 120px;
  border-radius: 2px;
  margin-top: 8px;
  margin-bottom: 0;
  float: right;
}

.form-body:after {
  content: '';
  display: table;
  clear: both;
}

/* フラッシュ ================================ */
.flash {
  padding: 10px 0;
  color: white;
  background: rgb(251, 170, 88);
  text-align: center;
  position: absolute;
  top: 64px;
  z-index: 10;
  width: 100%;
  border-radius: 0 0 2px 2px;
  font-size: 14px;
}

/* ---------------ここまで--------------- */
```
</details>

    CSSを編集出来たら、ビューの項目で編集した "top.html.erb"へ、更に記述を加えていきます。
    "top.html.erb"に下記のコードを記述してみましょう。

```   
<header>
  <div class="header-logo">
    TweetMemory
  </div>
  <ul class="header-menus">
    <li>
      TweetMemoryとは
    </li>
  </ul>
</header>

<div class="main top-main">
  <div class="top-message">
    <h2>今日の思い出を残そう。</h2>
    <p>まずは今の気持ちから</p>
  </div>
</div>
```
4. トップページを表示してみましょう！  
   最後にもう一度”localhost:3000/”でアクセスしてみましょう。  
   最初に確認したようにページが表示されれば成功です！  
   もしもエラーが出てしまったら、エラー表示ページを見てどこがエラーの原因であるのかを確認し、修正していきましょう。
   
   
   
   参考サイト：  
   【　[progate](https://prog-8.com/)　】
   【　[Railsガイド](https://railsguides.jp/)　】

        
       
     

    
