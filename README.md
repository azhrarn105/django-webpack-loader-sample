### 対象

- 「[Integrating Django and VueJs with Vue CLI 3 and Webpack Loader](https://medium.com/@rodrigosmaniotto/integrating-django-and-vuejs-with-vue-cli-3-and-webpack-loader-145c3b98501a)」

### 目的

- 上記のサイトの情報を元に、Django と Vue（VueCLI, Vuetify）による開発環境を構築してみる

### 試行時の環境

- Windows 10 Home
- Python 3.7.4
- npm 6.12.0

### 実行手順

1. このリポジトリを Clone（or Fork）後、直下の階層で Python の任意の仮想環境を構築  
  （理論上 venv でも virtualenv でも pipenv でも問題ないが、 venv で試行したのでその手順を示す）
   1. 以下コマンドを順に実行
      1. `> py -m venv venv`
      2. `> venv\Scripts\activate`
      3. `> pip install django django-webpack-loader pytz`
2. `frontend` ディレクトリへ移動し、以下コマンドを実行
   1. `> npm install`
3. `frontend` ディレクトリのまま、以下コマンドを実行し、 http://localhost:8080/ に Vuetify の初期画面が表示されることを確認
   1. `> npm run serve`
4. ルートディレクトリに戻り、Django の開発サーバーを起動し、 http://127.0.0.1:8000/ に Django経由で Vuetify の初期画面が表示されることを確認
  `> py manage.py runserver` 

### サンプルコード、手順を実行した際のポイント、変更点
- virtualenv のくだり ⇒ いつもの venv でもOK（pipでインストールするものを仮想化したいだけ）
- requirements.txt で諸々バージョンを指定しているが、それぞれ普通に1つずつ pip install で最新を入れても問題なかった
- createsuperuser は migrate 後にしかできないので、その順で（多分記事がミス）
- application.html の app タグ（`<app></app>`）は無くても動く
- vue.config.js のアドレス指定（ `0.0.0.0` ）は、全て `127.0.0.1` に変える