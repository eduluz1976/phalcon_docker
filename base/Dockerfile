FROM alpine:3.14

LABEL name="phalcon_base"
LABEL vcs-url="https://github.com/eduluz1976/phalcon_base"
LABEL maintainer="Eduardo Luz <eduardo at eduardo-luz dot com>"
LABEL version="1.0.0"
LABEL release-date="2021-08-05"

WORKDIR /srv

ENV TIMEZONE=UTC \
    LANGUAGE=en_US.UTF-8 \
    LANG=en_US.UTF-8 \
    LC_ALL=en_US.UTF-8 \
    TERM=xterm

RUN apk update \
    && apk upgrade --force \
    && apk add --no-cache bash bash-completion ca-certificates coreutils \
        musl-utils tzdata openssl curl git unzip php7 php7-phalcon php7-pdo \
        php7-mysqlnd php7-mysqli php7-pdo_mysql php7-mbstring php7-sodium \
        php7-pecl-yaml php7-zip php7-phar php7-pecl-redis \
    && update-ca-certificates 2>/dev/null || true \
    && ln -sf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime \ 
    && echo "${TIMEZONE}" | tee /etc/timezone \
    && rm -rf /tmp/* /var/cache/apk/* 


RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php');" \ 
    && mv composer.phar /usr/bin/composer 
