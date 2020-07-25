#最初のステージ
#---------------------------
#composerで結局php artisan migrateとか使うから、最終ステージに入れなきゃダメ
#というのは間違いでphp artisanはcomposer関係ない
FROM composer:1.10 as builder1

#ソースファイルのコピー
WORKDIR /var/www/html
RUN mkdir reread
COPY ./reread /var/www/html/reread

#書き込み可能にする
RUN chmod +w /var/www/html/reread

# パッケージインストール
# git colone後の初期設定
WORKDIR /var/www/html/reread
RUN composer install --no-dev \
&&php artisan key:generate

#２番目のステージ
#--------------------------
FROM node:12.16.2-alpine3.10 as node

WORKDIR /var/www/html
RUN mkdir reread
COPY --from=builder1 /var/www/html/reread /var/www/html/reread

WORKDIR /var/www/html/reread

RUN npm install \
&& npm rebuild node-sass \
&& npm run prod