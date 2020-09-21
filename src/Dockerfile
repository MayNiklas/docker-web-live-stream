ARG ARCH=
FROM ${ARCH}debian:buster-slim

RUN apt-get update && \
    apt-get -y upgrade

RUN apt-get install -y \
    build-essential \
    libpcre3 \
    libpcre3-dev \
    libssl-dev \
    zlib1g-dev \
    wget \
    unzip


WORKDIR /root
RUN wget http://nginx.org/download/nginx-1.19.2.tar.gz && \
    wget https://github.com/sergey-dryabzhinsky/nginx-rtmp-module/archive/dev.zip && \
    tar -zxvf nginx-1.19.2.tar.gz && \
    unzip dev.zip && \
    rm nginx-1.19.2.tar.gz dev.zip

WORKDIR /root/nginx-1.19.2
RUN ./configure \
  --with-http_ssl_module\
  --with-file-aio \
  --add-module=../nginx-rtmp-module-dev

RUN make
RUN make install 

VOLUME [ "/var/lib/streaming" ]
EXPOSE 1935 80 8080
COPY ./nginx.conf /usr/local/nginx/conf/nginx.conf
COPY ./html /usr/local/nginx/html

STOPSIGNAL SIGTERM
CMD ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]

