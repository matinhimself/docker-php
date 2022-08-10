ARG PHP_CLI_IMAGE


FROM ${PHP_CLI_IMAGE?}


ARG XDEBUG_VERSION



RUN echo ${XDEBUG_VERSION?}


RUN apt-get update -y -q;

RUN apt-get install -y -q \
    openssh-server \
    iputils-ping netcat;

RUN mkdir /var/run/sshd;

RUN apt-get install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip;

RUN pecl -q install xdebug-${XDEBUG_VERSION?}

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony

COPY ssh/id_rsa.pub /root/id_rsa.pub

RUN mkdir -p /root/.ssh \
 && cat /root/id_rsa.pub >> /root/.ssh/authorized_keys \
 && rm -rf /root/id_rsa.pub \
;

# COPY conf.d/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
# Moved this as mounted volume in docker-compose

RUN service ssh start
EXPOSE 22
CMD ["/usr/sbin/sshd","-D"]