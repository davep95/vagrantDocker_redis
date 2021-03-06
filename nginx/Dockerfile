FROM debian:wheezy

ENV DEBIAN_FRONTEND noninteractive

# Update the package repository
RUN \
  apt-get update && \
  apt-get upgrade -y && \
  apt-get install -y wget curl locales && \

# Configure timezone and locale
  echo "Europe/Madrid" > /etc/timezone && \
  dpkg-reconfigure -f noninteractive tzdata && \
  export LANGUAGE=es_ES.UTF-8 && \
  export LANG=es_ES.UTF-8 && \
  export LC_ALL=es_ES.UTF-8 && \
  locale-gen en_US.UTF-8 && \
  dpkg-reconfigure locales && \

  echo "deb http://packages.dotdeb.org wheezy all" >> /etc/apt/sources.list.d/dotdeb.org.list && \
  echo "deb-src http://packages.dotdeb.org wheezy all" >> /etc/apt/sources.list.d/dotdeb.org.list && \
  echo "deb http://packages.dotdeb.org wheezy-php56 all" >> /etc/apt/sources.list.d/dotdeb.org.list && \
  echo "deb-src http://packages.dotdeb.org wheezy-php56 all" >> /etc/apt/sources.list.d/dotdeb.org.list && \
  wget -O- http://www.dotdeb.org/dotdeb.gpg | apt-key add - && \
  apt-get update && \
  apt-get -y install nginx

COPY vhost.nginx.conf /etc/nginx/sites-enabled/default
ADD start.sh /start.sh

RUN \
 chmod a+x /start.sh && \
 echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \

# forward request and error logs to docker log collector
  ln -sf /dev/stdout /var/log/nginx/identity_access.log && \
  ln -sf /dev/stderr /var/log/nginx/identity_error.log

EXPOSE 80
ENTRYPOINT ["/start.sh"]
