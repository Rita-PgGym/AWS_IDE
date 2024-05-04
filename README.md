![image](https://github.com/Rita-PgGym/AWS_IDE/assets/159682878/85365cbb-2fe3-4680-8f0f-ef3664cfd083)![image](https://github.com/Rita-PgGym/AWS_IDE/assets/159682878/059d82b6-24c8-48ed-8764-da9d46af7bcd)# Laravel.10:CURD実装版
#### 作成日：2024-05-01
#### 更新日：
#### 環境：PHP8.2.15 Amazon Linux 2023 対象


---

## 【Laravel 0回目： Laravel 0回目： PHPフレームワーク/Laravelとは？】(16:00)
### 1. 開発環境構築
##### フレームワークとは
※フレームワークを使わないとゼロからプログラミングすることになる
　一つのファイルに長く記述する人、モジュール化（関数化）する人、オブジェクト指向（クラス）を取り入れる人等々、個人差がでる
　いろいろな作り方ができるのは良いことでもあるが、複数名で開発するときはこの自由さが規則性のないコードを生産してしまうというデメリットがある
　チームで規則を決めてもPHPは書けば動いてしまうので規則が守られない可能性が残ってしまう
　これを防ぐには、そこで一定のルールを守ることがもとめられる「フレームワーク」が有効

##### フレームワークのメリット
※実装の負荷軽減
　フレームワークには、便利な枠組み、関数、クラスなど必要な処理が用意されているので
　この用意されているものを使うだけで実装できる
　使い方（実装の仕方）を覚えればだれで作れる
　保守性、セキュリティ、規則性のあるコード、可読性の確保

##### フレームワークのデメリット
※PHPと比べると自由度は下がる
　関数、クラス、メソッド名など「フレーム」の規則に従わないと動作しない

##### なぜLaravelなのか
※人気があるフレームワークだから

##### Laravelの特徴
※学習コスト低い
・コードが読みやすく記述量少ない
・強力で簡単に技術できる入力チェック
・ログイン認証（ユーザー登録など）
・ページネーションが簡単に設置できる。
・本番環境へのアップロードが比較的ラク

【memo】最初からフレームワークを使うのではなく、PHPを学んでプログラミングを理解してから
　フレームワークを学び、使えるようになるのが良い

##### MVCパターン
※Model：データを扱う、PDO、app/以下
　View：表示する、PHPにHTMLを書いてたところ、echoとか
　Controller；メイン処理（if文、for文などを使ったロジックの部分）、app.Http/Controllers/以下


---
## 【Laravel 1回目： AWS AcademyのCloud9開発環境構築 と Laravel動作まで】(20:00)
### 1. Coud9開発環境構築
##### 1.00  AWSを使う理由
ローカルの環境の差異に振り回されない
クレジットカードを登録することなく、AWSが使える（100ドル分のクレジット付き！）

##### 1.01  AWS Academyにログイン
URL==> 　    https://awsacademy.instructure.com/login/canvas
Username==>　※メアド
パスワード==> ※わすれないようにね

##### 1.02  AWS Academy Learner Labに入る
ダッシュボードが表示されるので[AWS Academy Learner Lab]をクリック

##### 1.03  [モジュール]をクリック


##### 1.04  AWS Academy Learner Lab起動
[AWS Academy Learner Lab]の[AWS Academy Learner Lab を起動する]をクリック
　Vのくるくるが表示される
　左上　[AWS●]　　●はあか==>　あかる停止していることを示している(課金されていません)

##### 1.05  Labを開始する
右上に表示される　[▶Start Lab]をクリックする
　Vのくるくるが表示される（少し時間がかかる）
左上　[AWS●]　　●がみどりになる==>　みどりまるは起動していることを示している(課金されています)
　※ここまでが、学生用のメニューの処理


##### 1.06  コンソールのホーム画面を表示する
左上　[AWS●]　●はみどり　をクリックする
　※別タブに通常の（商用の）コンソール画面が表示される

##### 1.07  コンソールのホーム画面を表示して[Cloud9]サービスを利用する
一番上に表示される(AWSロゴの右横)のサービスの検索窓に「Cloud9」と入力する
または[最近アクセスしたサービス ]に表示される[Cloud9]をクリックしてもよい

##### 1.08  新規作成する
　[名前]：[DEMO_nn]
　[説明]：[開発環境構築n回目]
　[環境タイプ]：[新しいEC2インスタンス]
　[インスタンスタイプ]：[t2.micro(１GiB RAM＋1vCPU)]
　[プラットフォーム]：[Amazon Linux2023(推奨)]を選択
　[タイムアウト]：[30分]　
　　※30分何もしなかったら切断されるのでクレジットが減らなくなる
　[ネットワーク環境]：[セキュアシェル(SSH)]
　　※ここだけデフォルト値と違うので注意！
　[作成]ボタンクリック
　青い帯が表示されるので緑になるまで待つ（少しじかんがかかる）



##### 1.09  Cloud9 IDE(Integrated Development Environment統合開発環境)を設定する
新しく作成した環境の[Cloud9 IDE]の[開く]をクリック
別タブに作成した開発環境の設定画面が表示される


##### 1.10  隠しファイルを表示させる
　左のフレームの作成した環境名の横の歯車をクリック
　[Show Hidden Files]にチェックを付ける
　デフォルトはチェックが外れてる

##### 1.11  右上の歯車をクリック
　[Preference]タブが表示される
　左のメニューから[Experimental]をクリック
　Auto-Save Filesのモードを[After Delay]にする
　[Preference]タブはタブの[×]で閉じてOK
　※自動保存

##### 1.12  (途中まで作成して中断し再開した場合はターミナル開いていない)ターミナルを開く
下のターミナル(コマンドを打つ黒いところ)のタブのプラスをクリック
　[New Terminal]を選択


##### 1.13  ちょっとコマンドを打つ練習
さっそくターミナルでコマンドを打ってみよう！

```
php -v
```
```
node -v
```

【Tips】
- -v　でバージョンが見れます
- nodeはTailwindCSSを使うときに必要です


---
## 【Laravel 2回目：DB＋phpMyAdminの設定】
### 2. MariaDB 再構築
##### MariaDBデフォルト確認
```
sudo yum list installed | grep mariadb
```

##### Apache, MariaDBの起動
```
sudo systemctl start mariadb
```

```
sudo mysql_secure_installation
```
※最初コマンドで聞かれたら「空」のPasswordでEnter、Yes/Noを聞かれたら基本「Y」、NewPasswordは「root」にする。

##### MaridaDBの自動起動を有効化
```
sudo systemctl enable mariadb
```

```
sudo systemctl is-enabled mariadb
```

##### DB接続確認
★exitの後にはセミコロン;忘れないでね！


```
mysql -u root -p
```

```
root
```

```
exit;
```


---


### Composerインストール(3行一気にOK) 　【補足】1行ずつやる

```
curl -sS https://getcomposer.org/installer | php
```

```
sudo mv composer.phar /usr/bin/composer
```

```
composer
```
【確認】COMPOSERという文字がでっかく表示されていればOK！



### Laravelインストール
- バージョン指定する場合 → composer create-project "laravel/laravel=10.*" cms
- バージョン指定ない場合 → composer create-project laravel/laravel cms
- Laravel0.x 最新を指定 → composer create-project --prefer-dist laravel/laravel cms dev-master
```
composer create-project "laravel/laravel=10.*" cms 
```

### ディレクトリ移動(cmsはlaravelがフォルダ名です) ※2行一気にOK
```
cd cms
sudo composer update
```


### BuiltInサーバーを起動：動作確認
```
php artisan serve --port=8080
```


### Webサーバー＆Laravel画面の確認
- 4.1  [Preview]ボタン → [Preview Running Application]を選択
- 4.2  /resouces/views/welcome.blade.php を編集して確認しよう！
- 4.3  ブラウザ・更新で確認 →　変更確認できればOK


---


### <<重要ポイント>> [.env]ファイルを更新したら必ずWebサーバーを再起動！！

##### Webサーバー止める
 [ Ctl + C ]キー でWebサーバーを止める

##### Webサーバー起動（.envの再読み込み！）
```
php artisan serve --port=8080
```

-------



### ＜重要＞ AWS EC2環境では必須追記！！ → MAMP/XAMPPの場合は無視！
/app/Providers/ AppServiceProvider.php ファイルを修正
```
use Illuminate\Support\Facades\URL;    //この行を追加
public function boot() {
   URL::forceScheme('https');          //この行を追加
}
```


### データベース作成
```
mysql -u root -p
root [Enterキー]
create database c9;
exit;
```



##### .env（ファイル内の同じ箇所を上書き）
``` 
DB_CONNECTION=mysql
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=c9
DB_USERNAME=root
DB_PASSWORD=root
```


### phpMyAdmin設定
```
cd public

wget https://files.phpmyadmin.net/phpMyAdmin/5.1.2/phpMyAdmin-5.1.2-all-languages.zip

unzip phpMyAdmin-5.1.2-all-languages.zip

cd ..

```

---

### ＜phpMyAdmin確認手順＞
- 5.1 publicフォルダ内に「phpMyAdmin-*.*.*-all-languages」フォルダが作成される 
- 5.2 フォルダ名が長いので「phpMyAdmin」に変更
- 5.3「Preview」でサイトを開き、URLの最後に「phpMyAdmin/index.php」をつけてEnterキーを押す
- 5.4 URL例： https://＊＊＊＊＊＊.cloud9.us-east-1.amazonaws.com/phpMyAdmin/
- 5.5 phpMyAdmin画面が表示されたら： ユーザー名・パスワードともに「root」を入力してログイン
- 5.6 ログインできればOK


---

## 【Laravel 3回目：Bleeze/認証機能】
### 3. Auth( ユーザー登録・認証画面とテンプレート作成 )
―  Laravel0.x ~ 以降対応
-  laravel/breeze のインストール
- 【注意】Laraveのバージョンが違うとErrorになります！！
-  コマンド打って、yes/no がでたらyes で！！

#### 0. ＜＜重要＞＞cmsの中で実行
```
cd cms
```

#### 1. Laravel 10.x の場合
```
# sudo composer require laravel/breeze --dev
composer require laravel/breeze:*
```

#### 2. artisan コマンドを実行
```
php artisan breeze:install
```

#### 3.以下が表示されます
「 Blade with Alpine 」をキーボードの↑↓で選択してEnter

#### 4.Dark Mode対応？
 Yes 選択してEnter

#### 5.テストライブラリの選択
PHPUnit を選択してEnter

#### 6. HTML/CSS/JSをビルド（構築👉フロントで修正があるたびにビルド）
```
npm run build
```

#### 7．テーブル作成
```
php artisan migrate
```

【確認】ログイン機能・画面が作成されました、画面で確認！。


---


#### 8．Login画面とRegister画面にリンクを追加( 2ファイル修正)

- /resources/views/auth/register.blade.php
- /resources/views/auth/login.blade.php


##### `<x-guest-layout>`の次「2行目」に以下を貼り付け ... 
```
<!-- 以下を追加 -->
@if (Route::has('login'))
    <div class="hidden fixed top-0 right-0 px-6 py-4 sm:block">
        @auth
            <a href="{{ url('/dashboard') }}" class="text-sm text-gray-700 dark:text-gray-500 underline">Dashboard</a>
        @else
            <a href="{{ route('login') }}" class="text-sm text-gray-700 dark:text-gray-500 underline">Log in</a>

            @if (Route::has('register'))
                <a href="{{ route('register') }}" class="ml-4 text-sm text-gray-700 dark:text-gray-500 underline">Register</a>
            @endif
        @endauth
    </div>
@endif
```

【確認】画面を変えたのでnpm run buildを実行しよう！
```
npm run build
```

【確認】Login画面とRegister画面の右上にLoginとRegister　リンクが追加されていることを確認しよう！


---

## 【Laravel 4回目：Laravel/マイグレーション】
### 4. データ構造を作成（テーブル作成） 
##### 1. booksテーブルを作成（マイグレーションファイル作成）
```
php artisan make:migration create_books_table --create=books
```
【確認】databases/migrations/にyyyy_mm_dd_hhmmss_create_books_table.php　が作成されていることを確認しよう！

【Tips】
- トランザクションテーブル：データが積みあがっていく（増えていく）
- マスターテーブル：データは固定 (例)都道府県テーブルなど


 
  


##### 2. [年]_[月]_[日]_[時分秒]_create_books_table.phpが作成されます
- /database/migrations/フォルダの中に生成されます
- 生成されたファイルを開き、public function up(){...}の中を追加修正
```
public function up()
    {
        Schema::create('books', function (Blueprint $table) {
            $table->id();
            //** ↓ 下をコピー ↓ **
            
            $table->string('item_name');     //ここを追加
            $table->integer('item_number');  //ここを追加
            $table->integer('item_amount');  //ここを追加
            $table->date('published');       //ここを追加
            
            //** ↑ 上をコピー ↑ **
            $table->timestamps();
        });
}
```


##### 3．マイグレーションを実行（テーブル作成）
```
php artisan migrate
```



##### 4．MySQL DBに作成されたテーブルを確認 (php+MyAdminの画面で)
【確認】phpMyAdminでc9の中のbooksテーブルの構造に追加した4行があることを確認しよう！

phpMyAdmin URL例： 
```
https://＊＊＊＊＊＊.cloud9.us-east-1.amazonaws.com/phpMyAdmin/
```

##### 5．ModelとControllerを一括作成
- ModelとはDB周りを簡単に扱えるようにする部分を書くファイル
- Controllerとは処理の部分(if文とかfor文とか)を書くファイル
```
php artisan make:model Book -cr
```

【Tips】テーブル名とモデル名
- テーブル名　終わりにsが付く　（例）users、books、items
- モデル名　終わりのsをとって先頭文字を大文字にする　　（例）User、Book、Item

##### 6．生成されたファイルを確認
【確認】生成されたファイルを確認しよう！次の2つのファイルが生成されます。

- /app/models/Book.php が作成されます。これはMVCモデルのM(Model)です。
- /app/Http/Controllers/BookController.php が生成されます＋空のメソッドも自動で生成されます。これはMVCモデルのC(Contorler)です。ここには処理を書くところです。

###### [ 参考Documents ]

[Laravel Document マイグレーション](https://readouble.com/laravel/10.x/ja/migrations.html)

[Laravel Document コントロール](https://readouble.com/laravel/10.x/ja/controllers.html)

[Laravel Document モデル](https://readouble.com/laravel/10.x/ja/eloquent.html)


---

## 【Laravel 5回目：ルーティング】
### 5. ルート定義（ルーティング）

【Tips】ルーティング
- URLと「処理」or「画面」を紐づけすること
- cms/routes/web.php　がルーティングしてくれる
- ルーティングとはURLを叩いたら、どのファイルに紐づけること


##### 1. /routes/web.php に 以下コードを貼り付けます。
```
<?php
use App\Http\Controllers\ProfileController;
use Illuminate\Support\Facades\Route;
use Illuminate\Http\Request; //Add
use App\Http\Controllers\BookController; //Add

//本：ダッシュボード表示(books.blade.php)
Route::get('/', [BookController::class,'index'])->middleware(['auth'])->name('book_index');
Route::get('/dashboard', [BookController::class,'index'])->middleware(['auth'])->name('dashboard');

//本：追加 
Route::post('/books',[BookController::class,"store"])->name('book_store');

//本：削除 
Route::delete('/book/{book}', [BookController::class,"destroy"])->name('book_destroy');

//本：更新画面
Route::post('/booksedit/{book}',[BookController::class,"edit"])->name('book_edit'); //通常
Route::get('/booksedit/{book}', [BookController::class,"edit"])->name('edit');      //Validationエラーありの場合

//本：更新画面
Route::post('/books/update',[BookController::class,"update"])->name('book_update');

/**
* 「ログイン機能」インストールで追加されています 
*/
//Route::get('/dashboard', function () {
//    return view('dashboard');
//})->middleware(['auth', 'verified'])->name('dashboard');

Route::middleware('auth')->group(function () {
    Route::get('/profile', [ProfileController::class, 'edit'])->name('profile.edit');
    Route::patch('/profile', [ProfileController::class, 'update'])->name('profile.update');
    Route::delete('/profile', [ProfileController::class, 'destroy'])->name('profile.destroy');
});

require __DIR__.'/auth.php';
```

###### [ 参考Documents ]
[Laravel Document ルーティング](https://readouble.com/laravel/10.x/ja/routing.html)

---

## 【Laravel 6回目：View・コンポーネント】12:45
### 6. View

【Tips】MVCモデルのV(View)＝画面表示の部分に入ります！ちょっと複雑になります…がんばろ！
- Laravel9.1以降CSSフレームワークのBootstrapがデフォルトで選択できなくなった
- コンポーネント化の知識が必須になった⇒覚えるしかないが、難しい話ではない！
- CSSはTailwind CSSがデフォルトになった⇒Tailwind CSSのCheet Sheetがあるので見てみよう！
- コンポーネントは、includeで部品を読み込む、みたいにとらえると分かりやすいかも（まだわからんけど）



##### 1. /resources/views/components/collection.blade.php を作成
【Tips】MVCモデルのV(View)に入ります！ちょっと複雑になります…がんばろ！
-/resources/views/components/ にはよく使うものを部品としてを入れる⇒ここだけ直せばよい(メンテナンス性アップ)
-表示用のファイルの拡張子は必ず　.blade.php　にする⇒この拡張子にしないと使えない

 
- /resources/views/components/　で新規ファイル作成⇒ファイル名はcollection.blade.php
- 以下のコードを貼り付ける
```
<div class="flex justify-between p-4 items-center bg-blue-500 text-white rounded-lg border-2 border-white">
  <div>{{ $slot }}</div>
  <button>×</button>
</div>
```


##### 2. /resources/views/components/errors.blade.php を作成 
- /resources/views/components/　で新規ファイル作成⇒ファイル名は　errors.blade.php
- 入力エラーのチェックの部品を作ろう！一つ部品を作ってそれを再利用していこう！
- 以下のコードを貼り付ける
```
<!-- resources/views/components/errors.blade.php -->
@if (count($errors) > 0)
    <!-- Form Error List -->
    <div class="flex justify-between p-4 items-center bg-red-500 text-white rounded-lg border-2 border-white">
        <div><strong>入力した文字を修正してくた?さい。</strong></div> 
        <div>
            <ul>
            @foreach ($errors->all() as $error)
                <li>{{ $error }}</li>
            @endforeach
            </ul>
        </div>
    </div>
@endif
```


##### 3. /resources/views/books.blade.php を作成
- /resources/views/　で新規ファイル作成⇒ファイル名はbooks.blade.php
- これは部品ではなくテンプレートを作るよ！
- このファイルは　上で作った　collection.blade.php　や　errors.blade.php　を読み込んで使うテンプレート
- <x-app-layout></x-app-layout>　で囲んだところがコンポーネントを読み込むところ（よく分からん）
- 以下のコードを貼り付ける
```
<!-- resources/views/books.blade.php -->
<x-app-layout>

    <!--ヘッダー[START]-->
    <x-slot name="header">
        <h2 class="font-semibold text-xl text-gray-800 leading-tight">
            <form action="{{ route('book_index') }}" method="GET" class="w-full max-w-lg">
                <x-button class="bg-gray-100 text-gray-900">{{ __('Dashboard') }}</x-button>
            </form>
        </h2>
    </x-slot>
    <!--ヘッダー[END]-->
            
        <!-- バリデーションエラーの表示に使用-->
       <x-errors id="errors" class="bg-blue-500 rounded-lg">{{$errors}}</x-errors>
        <!-- バリデーションエラーの表示に使用-->
    
    <!--全エリア[START]-->
    <div class="flex bg-gray-100">

        <!--左エリア[START]--> 
        <div class="text-gray-700 text-left px-4 py-4 m-2">
            
            <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                <div class="p-6 bg-white border-b border-gray-500 font-bold">
                    本を管理する
                </div>
            </div>


            <!-- 本のタイトル -->
            <form action="{{ url('books') }}" method="POST" class="w-full max-w-lg">
                @csrf
                  <div class="flex flex-col px-2 py-2">
                   <!-- カラム１ -->
                    <div class="w-full md:w-1/1 px-3 mb-2 md:mb-0">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                       Book Name
                      </label>
                      <input name="item_name" class="appearance-none block w-full text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" type="text" placeholder="">
                    </div>
                    <!-- カラム２ -->
                    <div class="w-full md:w-1/1 px-3">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                        金額
                      </label>
                      <input name="item_amount" class="appearance-none block w-full text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500" type="text" placeholder="">
                    </div>
                    <!-- カラム３ -->
                    <div class="w-full md:w-1/1 px-3 mb-2 md:mb-0">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                        数
                      </label>
                      <input name="item_number" class="appearance-none block w-full text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500" type="text" placeholder="">
                    </div>
                    <!-- カラム４ -->
                    <div class="w-full md:w-1/1 px-3 mb-6 md:mb-0">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                        発売日
                      </label>
                      <input name="published" type="date" class="appearance-none block w-full text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500">
                    </div>
                  </div>
                  <!-- カラム５ -->
                  <div class="flex flex-col">
                      <div class="text-gray-700 text-center px-4 py-2 m-2">
                             <x-button class="bg-blue-500 rounded-lg">送信</x-button>
                      </div>
                   </div>
            </form>
        </div>
        <!--左エリア[END]--> 
    
    
    <!--右側エリア[START]-->
    <div class="flex-1 text-gray-700 text-left bg-blue-100 px-4 py-2 m-2">
        <x-collection>テスト１</x-collection>
        <x-collection>テスト２</x-collection>
        <x-collection>テスト３</x-collection>
    </div>
    <!--右側エリア[[END]-->       

</div>
 <!--全エリア[END]-->

</x-app-layout>
```


##### 4. /resources/views/components/button.blade.php を作成
- 以下のコードを貼り付ける
```
<button {{ $attributes->merge(['type' => 'submit', 'class' => 'inline-flex items-center px-4 py-2 bg-gray-800 border border-transparent rounded-md font-semibold text-xs text-white uppercase tracking-widest hover:bg-gray-700 active:bg-gray-900 focus:outline-none focus:border-gray-900 focus:ring ring-gray-300 disabled:opacity-25 transition ease-in-out duration-150']) }}>
    {{ $slot }}
</button>
```

##### 5. componentファイルとbladeファイルをBuild!!
- bladeファイルとcomponentファイルを合体させます
- JS/CSS(TailwindCSS)も同時にBuildされます
- <重要>　フロント側の修正したら必ず実行してください⇒ブラウザで確認する前にこのコマンドを打つことを習慣にしよう！
```
npm run build
```

###### 参考Documents
[Laravel Document View](https://readouble.com/laravel/10.x/ja/views.html)

---

## 【Laravel 7回目：コントローラー①（登録処理）】(28:00)
### 7. Controller
【Tips】Controllerは処理！
- Controller　には、PHPやJSで書いていたif文、for文などでcodingしていた処理を書きます！
  


##### 1. app/Http/Controllers/BookController.php を開く
- このControllerでValidatorを使えるようにする
- このControllerでAuthを使えるようにする
```
# use App\Models\Book;
# use Illuminate\Http\Request;

use Illuminate\Support\Facades\Validator; //この2行を追加！
use Illuminate\Support\Facades\Auth;      //この2行を追加！
```
上記 または 以下どちらか
```
use Validator;  //この2行を追加！
use Auth;       //この2行を追加！
```


##### 2. /app/Http/Controllers/BookController.php を開く
- [データ登録処理] public function store の中に以下を追加
```
public function store(Request $request)
{
   //** ↓ 下をコピー ↓ **
   
      
    //バリデーション
    $validator = Validator::make($request->all(), [
         'item_name' => 'required|min:3|max:255',
         'item_number' => 'required | min:1 | max:3',
         'item_amount' => 'required | max:6',
         'published'   => 'required',
    ]);

    //バリデーション:エラー 
    if ($validator->fails()) {
        return redirect('/')
            ->withInput()
            ->withErrors($validator);
    }
    //以下に登録処理を記述（Eloquentモデル）

  // Eloquentモデル
  $books = new Book;
  $books->item_name   = $request->item_name;
  $books->item_number = $request->item_number;
  $books->item_amount = $request->item_amount;
  $books->published   = $request->published;
  $books->save(); 
  return redirect('/');
  
  
   //** ↑ 上をコピー ↑ **
}
```
【Tips】バリデーション
- Validator　部分は、基本コピペでOK！
- 項目(name、number等）は自分が作りたいものに合わせて修正したり、追加したりすればOK

【Tips】バリデーションエラー
- ここも、基本コピペでOK！
- 戻す先　return redirect('/')　を自分の戻したいところに変えればOK！

【Tips】 登録処理部分(Eloquentモデル)
-  $books = new Book;　テーブル名はbooks、モデルはBook、これはテーブルにアクセスするためのルール！
-  飛んできたものをbooksテーブルのそれぞれの値に渡し、$books->save();　でテーブルに保存する
-  SQL文を打たなくていい、ということです

---

## 【Laravel 8回目：コントローラー②（表示処理）】
##### 3. /app/Http/Controllers/BookController.php を開く
- [データ取得・表示処理] public function index() 内に以下を追加

```
public function index() {
   //** ↓ 下をコピー ↓ **    
   
    $books = Book::orderBy('created_at', 'asc')->get();
    return view('books', [
        'books' => $books
    ]);
    
    //** ↑ 上をコピー ↑ **
}
```

【Tips】 データの取得処理
-  Book::　でbooksテーブルにアクセスできる
-  orderBy('カラム名', '昇順・降順の指定')　でソート指定する
-  get()でデータを取得する


##### 4. /resources/views/books.blade.php を開く
- books.blade.php の ***「右側エリア」*** を全て上書き！！
```
    <!--右側エリア[START]-->
    <div class="flex-1 text-gray-700 text-left bg-blue-100 px-4 py-2 m-2">
         <!-- 現在の本 -->
        @if (count($books) > 0)
            @foreach ($books as $book)
                <x-collection id="{{ $book->id }}">{{ $book->item_name }}</x-collection>
            @endforeach
        @endif
    </div>
    <!--右側エリア[[END]-->     
```

【Tips】 データの表示理
-  bladeテンプレートでは　@if、@endif、@for、@endfor、@foreach、@endforeach　が用意されている
-  blade.php　(テンプレート)　の中で使える関数のことを　ディレクティブといいます（よく分からん）
-  Laravel　ディレクティブ　で検索してみよう！
-   (count($books) > 0)　で　count関数を使って　$books　がいくつなのか（つまりレコード数はいくつかのか）を数えて0より大きければ　foreach関数でその数分だけ回す

---

## 【Laravel 9回目： コントローラー③（削除処理）】
##### 5. /resources/views/components/collection.blade.php を開く
- collection.blade.php 内のcomponentを以下CODEに ***全て上書き！！*** 
```
<!-- 本: 削除ボタン -->
<div class="flex justify-between p-4 items-center bg-blue-500 text-white rounded-lg border-2 border-white">
  <div>{{ $slot }}</div>
  
    <div>
    <form action="{{ url('booksedit/'.$id) }}" method="POST">
         @csrf
         
        <button type="submit"  class="btn bg-blue-500 rounded-lg">
            更新
        </button>
        
     </form>
  </div>
  
  <div>
    <form action="{{ url('book/'.$id) }}" method="POST">
         @csrf
         @method('DELETE')
        
        <button type="submit"  class="btn bg-blue-500 rounded-lg">
            削除
        </button>
        
     </form>
  </div>

</div>
```
【Tips】 CSRF攻撃対策
-  クロスサイトリクエストフォージェリ攻撃からアプリケーションを保護するためにPOSTの時は必ず<form>タグ内に　@csrfと書く
-  これもblade.php　(テンプレート)　の中で使える関数、ディレクティブです



##### 6. /app/Http/Controllers/BookController.php を開く
- [データ削除処理] public function destroy に以下コードを追加
```
public function destroy(Book $book)
{
   //** ↓ 下をコピー ↓ **    
    
    $book->delete();       //追加
    return redirect('/');  //追加
    
     //** ↑ 上をコピー ↑ **
}
```

- [Errorが出た場合] 以下のコマンドでdeleteになっているか確認
```
php artisan route:list -v
```

【Tips】 ブラウザのソースコードを見てみよう！
-  PHPはサーバー上でcode生成しし、その結果がブラウザに送付されてくる。ソースコードを見ると分かりやすい


###### [ 参考Documents ]

[Laravel Document コントロール](https://readouble.com/laravel/10.x/ja/controllers.html)


---

## 【Laravel 10回目： コントローラー④（更新処理）】(17:00)
### 8. 更新機能を作成 
##### 1. [更新機能] view画面を作成
- /resources/views/booksedit.blade.php を新規作成
- 以下コードを貼り付ける
```
<!-- resources/views/booksedit.blade.php -->
<x-app-layout>

    <!--ヘッダー[START]-->
    <x-slot name="header">
        <h2 class="font-semibold text-xl text-gray-800 leading-tight">
            <form action="{{ route('book_index') }}" method="GET" class="w-full max-w-lg">
                <x-button class="bg-gray-100 text-gray-900">{{ __('Dashboard') }}：更新画面</x-button>
            </form>
        </h2>
    </x-slot>
    <!--ヘッダー[END]-->
            
        <!-- バリデーションエラーの表示に使用-->
        <x-errors id="errors" class="bg-blue-500 rounded-lg">{{$errors}}</x-errors>
        <!-- バリデーションエラーの表示に使用-->
    
    <!--全エリア[START]-->
    <div class="flex bg-gray-100">

        <!--左エリア[START]--> 
        <div class="text-gray-700 text-left px-4 py-4 m-2">
            
            <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                <div class="p-6 bg-white border-b border-gray-500 font-bold">
                    本を管理する
                </div>
            </div>


            <!-- 本のタイトル -->
            <form action="{{ url('books/update') }}" method="POST" class="w-full max-w-lg">
                @csrf
                
                  <div class="flex flex-col px-2 py-2">
                   <!-- カラム１ -->
                    <div class="w-full md:w-1/1 px-3 mb-2 md:mb-0">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                       Book Name
                      </label>
                      <input name="item_name" value="{{$book->item_name}}" class="appearance-none block w-full text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" type="text" placeholder="">
                    </div>
                    <!-- カラム２ -->
                    <div class="w-full md:w-1/1 px-3">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                        金額
                      </label>
                      <input name="item_amount" value="{{$book->item_amount}}" class="appearance-none block w-full text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500" type="text" placeholder="">
                    </div>
                    <!-- カラム３ -->
                    <div class="w-full md:w-1/1 px-3 mb-2 md:mb-0">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                        数
                      </label>
                      <input name="item_number" value="{{$book->item_number}}" class="appearance-none block w-full text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500" type="text" placeholder="">
                    </div>
                    <!-- カラム４ -->
                    <div class="w-full md:w-1/1 px-3 mb-6 md:mb-0">
                      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2">
                        発売日
                      </label>
                      <input name="published" type="date" value="{{$book->published}}" class="appearance-none block w-full text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500">
                    </div>
                  </div>
                  <!-- カラム５ -->
                  <div class="flex flex-col">
                      <div class="text-gray-700 text-center px-4 py-2 m-2">
                             <x-button class="bg-blue-500 rounded-lg">更新</x-button>
                      </div>
                   </div>
                <!-- id値を送信 -->
                <input type="hidden" name="id" value="{{$book->id}}">
                <!--/ id値を送信 -->
            </form>
        </div>
        <!--左エリア[END]--> 
    
    
    <!--右側エリア[START]-->
    <div class="flex-1 text-gray-700 text-left bg-blue-100 px-4 py-2 m-2">
      
    </div>
    <!--右側エリア[[END]-->       

</div>
 <!--全エリア[END]-->

</x-app-layout>
```


##### 2．[更新機能] コントローラー
- /app/Http/Controllers/BookController.phpを開く
- 以下コードを ***edit*** に追加する
```   
   public function edit(Book $book)
    {
        //** ↓ 下をコピー ↓ **
        
        //{books}id 値を取得 => Book $books id 値の1レコード取得
        return view('booksedit', ['book' => $book]);
        
        //** ↑ 上をコピー ↑ **!
    }
```

###### 更新画面へのルーティングは以下(/routes/web.php)
```
Route::post('/booksedit/{book}',[BookController::class,"edit"])->name('book_edit'); //通常
Route::get('/booksedit/{book}', [BookController::class,"edit"])->name('edit');      //Validationエラーありの場合
```


##### 3．[更新機能] 更新処理
- /app/Http/Controllers/BookController.php を開く
- 以下コードを ***update*** メソッドに追加する
``` 
    public function update(Request $request, Book $book)
    {
      //** ↓ 下をコピー ↓ **


        //バリデーション
         $validator = Validator::make($request->all(), [
             'id' => 'required',
             'item_name' => 'required|min:3|max:255',
             'item_number' => 'required|min:1|max:3',
             'item_amount' => 'required|max:6',
             'published' => 'required',
        ]);
        //バリデーション:エラー
         if ($validator->fails()) {
             return redirect('/booksedit/'.$request->id)
                 ->withInput()
                 ->withErrors($validator);
        }
        
        //データ更新
        $books = Book::find($request->id);
        $books->item_name   = $request->item_name;
        $books->item_number = $request->item_number;
        $books->item_amount = $request->item_amount;
        $books->published   = $request->published;
        $books->save();
        return redirect('/');
        
        
        //** ↑ 上をコピー ↑ **!
    }

【確認】 通し確認
-  ここまででCRUDができるようになっているので通しで確認してみよう！Create⇒Read⇒Update⇒Delete


---

## 【Laravel 11回目： Laravel 11回目： ページネーション】
### 9. Pagenation機能

##### 1. コントローラ：indexメソッドの修正
- BookController.phpの ***indexメソッド*** に以下コードを上書き
- paginate(3); の箇所だけ変わります
- paginate(表示件数); ()の中に何件表示するかを書く

```
    public function index()
    {
        $books = Book::orderBy('created_at', 'asc')->paginate(3);
        return view('books', [
            'books' => $books
        ]);
    }
```


##### 2. Viewにリンクを生成するコードを追加
- books.blade.php に 以下コードを追加します。
- 右側エリアの一番下にページ送りを表示したいので右側エリアの最後の@endifのあとに追加
- linksメソッドを使う

```
        <div>
            {{ $books->links()}}
        </div>
```


---

## 【Laravel 12回目： Auth：認証しないと見れない設定】(11:54)
- ログアウトして　https://***.amazonaws.com/booksedit/2　と叩くと見えてしまう(最後の数字はbooksテーブルに存在しているレコードのID)
- この状態に対してログインしたユーザーにしか見せないようにす（PHPではセッションを使って実現していた部分）⇒Laravelはこの機能が準備してある
- ->middleware(['auth']) を追加すれば簡単にできる


---


## 【Laravel  13回目：自分が登録したデータのみ（表示・更新・削除）1ｘ1】(20:00)
### 10. ユーザーがログインしたらユーザーが登録した本のみ表示
- １ユーザー ✕ １サービス
- phpMyAdminではなく、migrationファイルから変更することが大事！


##### 1. ユーザーidを登録できるようにbooksテーブルを変更
- /database/migrations/[yyyy_mm_dd_hhiiss]_create_books_table.php に以下***１行を追加します***。
```
$table->bigInteger('user_id'); //追加:user_id
```

##### 2. テーブルを再構築する
- テーブルをリセットして、再構築するコマンド
```
php artisan migrate:refresh
```

##### 3．再構築されたbooksテーブルを確認 
【確認】 テストデータが消えている
-  refresh　はresetして再構築しているのでテストデータが消えている⇒booksデータもuserデータも消えているので再度登録すること


phpMyAdmin
```
http://localhost:8080/　　⇒なぜlocalhost:8080/　なのか不明・・・(間違い？)
```


##### 5. コントローラ「BooksController@index」を修正
- 以下indexメソッドの「Book」モデルの条件を変えます
- "where('user_id',Auth::user()->id)->"を追加して認証してる人のAuthIDを条件に追加しています
```
 $books = Book::where('user_id',Auth::user()->id)->orderBy('created_at', 'asc')->paginate(3);
```


##### 6. コントローラ「BooksController@store」に追加
```
$books->user_id  = Auth::user()->id; //追加のコード
```

##### 7. コントローラ「BooksController@update」を修正
```
$books = Book::where('user_id',Auth::user()->id)->find($request->id);
```

##### 8. コントローラ「BooksController@edit」を修正
- 修正範囲が多いのでeditメソッドを上書き
```
public function edit($book_id)
{
    $books = Book::where('user_id',Auth::user()->id)->find($book_id);
    return view('booksedit', ['book' => $books]);
}
 ```
 
 ---
 
 
## 補足
####  ★Laravel Document
https://readouble.com/laravel/10.x/ja/

#### ★Auth(認証)USER情報取得
  ```
//Authを使うControllerに追加してあること
use Illuminate\Support\Facades\Auth;

// 現在認証しているユーザーを取得
$user = Auth::user();

// 現在認証しているユーザーのIDを取得
$id = Auth::id();
```

### ★【保存版】バリデーションルールのまとめ
https://www.wakuwakubank.com/posts/376-laravel-validation/


#### ★Validatorの日本語対応方法例1
https://utubou-tech.com/laravel_validation_ja/
  

#### ★Validatorの日本語対応方法例2
```
  $rulus = [
    'name' => 'required',
    'age' => 'integer | between:0,150',
    'sex' => ['max:1', 'regex:/^[男|女]+$/u'],
  ];

  $message = [
    'name.required' => '名前を入力してください',
    'age.numeric' => '整数で入力してください',
    'age.between' => '0～150で入力してください'
    'sex.regex' => '男か女で入力してください',
  ];

  $validator = Validator::make($request->all(), $rulus, $message);
  ```

  ####  ★Validatorの日本語対応方法例3 FormRequestクラスを使った場合
  https://qiita.com/daisu_yamazaki/items/e44d4b744d9d5f9bc8b3
 


  
 #### ★データテーブルをJOINしてデータを取得したい
 
 ***参考URL***
 https://migisanblog.com/laravel-eloquent-relation/
 
 ***Qiita参考URL***
 https://qiita.com/zaburo/items/d665804f8ea850502c64
 
