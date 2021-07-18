# Laravel Base コンテナ

この記事を参考にしながら構築していった。
https://qiita.com/ucan-lab/items/56c9dc3cf2e6762672f4#%E3%82%A6%E3%82%A7%E3%83%96%E3%82%B5%E3%83%BC%E3%83%90%E3%83%BCweb%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%82%92%E4%BD%9C%E3%82%8B

## コンテナに入る

docker compose exec app bash
docker compose exec web bash

## Laravel を動かすために必要な機能が入っているかを確認する

### apt-get update

どうも Debian 系を使ったときにはお決まりで流すみたい。
けど流そうとしたときに怒られた。
どうも Docker の問題みたいで、割り当てた disk サイズに収まらんと怒られてたみたい。
docker desktop の方のディスクサイズ割り当てを大きくしてやったら解消した。
参考 →https://qiita.com/yukia3e/items/6e2536dd90d34a8b01cc

### PHP のバージョンの確認

    php -v

### Composer バージョンの確認

    composer -v

### nginx バージョンの確認

    docker compose exec web nginx -v

## Docker で構築されているネットワークを確認する

    docker network list

## ↑ で確認したネットワークの構成情報の詳細を確認する

    docker network inspect　ネットワーク名

今回はこれ。→laravel_default
