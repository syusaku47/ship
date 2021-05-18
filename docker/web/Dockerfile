FROM centos:7

ENV HOSTNAME web-server

RUN yum check-update; \
        yum clean all; \
        yum update -y; \
        yum install -y vim net-tools; \
        yum install -y epel-release; \
        : '# Repository install'&& \
        rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm; \
        : '# Apache 2.4 install' && \
        yum install -y httpd mod_ssl; \
        systemctl enable httpd.service; \
        mkdir /var/www/app; \
        : '# PHP 8.0.6 install' && \
        yum -y install php80 php80-php php80-php-bcmath php80-php-json php80-php-mbstring php80-php-pdo php80-php-xml php80-php-mysqlnd php80-pecl-zip php80-pear --enablerepo=remi-php80; \
        : 'phpコマンドが使えるようにシンボリックリンクを貼る' && \
        ln -sf /usr/bin/php80 /usr/bin/php; \
        : '# PHP composer install' && \
        curl https://getcomposer.org/installer | php && \
        mv -i composer.phar /usr/local/bin/composer && \
        : '# zip install' && \
        yum install -y zip; \
        : '# unzip install' && \
        yum install -y unzip; \
        : '# git install' && \
        yum install -y git; \
        : '# cron install' && \
        yum install -y crontabs; \
        : '# ImageMagick install' && \
        yum install -y ImageMagick; \
        : '# ImageMagick-devel install' && \
        yum install -y ImageMagick-devel; \
        : '# ipa-font install' && \
        yum install -y ipa-gothic-fonts ipa-mincho-fonts ipa-pgothic-fonts ipa-pmincho-fonts; \
        : '# composer' && \
        php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
        php composer-setup.php; \
        php -r "unlink('composer-setup.php');"; \
        mv -f composer.phar /usr/local/bin/composer; \
        : '# node.js install' && \
        yum install -y https://rpm.nodesource.com/pub_14.x/el/7/x86_64/nodesource-release-el7-1.noarch.rpm; \
        yum -y install nodejs; \
        npm update -g npm; \

