ARG PHP_FPM_VERSION
FROM ${PHP_FPM_VERSION?}
ARG XDEBUG_VERSION
RUN pecl install xdebug-${XDEBUG_VERSION?} \
    && docker-php-ext-enable xdebug

