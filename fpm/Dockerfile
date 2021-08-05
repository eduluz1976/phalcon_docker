FROM eduluz1976/phalcon_base:1.0.0

LABEL name="phalcon_fpm"
LABEL vcs-url="https://github.com/eduluz1976/phalcon_docker"
LABEL maintainer="Eduardo Luz <eduardo at eduardo-luz dot com>"
LABEL version="1.0.0"
LABEL release-date="2021-08-05"

WORKDIR /srv

RUN apk update \
    && apk add --no-cache php7-fpm

COPY www.conf /etc/php7/php-fpm.d/

EXPOSE 9000

# start PHP-FPM
CMD [ "php-fpm", "-F"]
