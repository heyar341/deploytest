FROM base_image as base

FROM nginx:1.16.1-alpine

COPY ./default.conf /etc/nginx/conf.d/default.conf
COPY --from=base /var/www/html/reread/public /var/www/html/reread/public