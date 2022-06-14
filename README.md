## 概要

Dockerを用いて、WordPressとNuxt.jsのイメージを作成し、ヘッドレス運用するためのDockerfileを用意する

## 作業手順

### 1. WordPressの構築まで
#### 1.1. リポジトリのクローン

#### 1.2. ディレクトリに移動し、Dockerイメージをビルド

``` bash

docker build -t nodewordpress .
```

#### 1.3. コンテナを起動


``` bash
docker-compose up -d --build
```

#### 1.4. WordPressの初期設定をコマンドで実施

``` bash
docker-compose exec wordpress wp core install --url=localhost --title='WordPress Sitee' --admin_user=admin --admin_email=itezora.nonoha@gmail.com --allow-root
```

この後、Admin Passwordが表示されるので、一応退避させておくと良いかも。


### 2. 動作確認用のダミー記事を投入する
#### 2.1. コンテナに入る

``` bash
docker-compose exec wordpress bash
```

#### 2.2. プラグインをインストール

``` bash
wp plugin install wordpress-importer --activate --allow-root
```

#### 2.3. ダミー記事を取得

``` bash
curl -O https://raw.githubusercontent.com/WPTRT/theme-unit-test/master/themeunittestdata.wordpress.xml
```

#### 2.4. ダミー記事を投入

``` bash
wp import themeunittestdata.wordpress.xml --authors=create --allow-root
```

> 2分くらい掛かる
