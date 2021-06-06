FROM alpine:3.13

# enabled Alpine's official community repository
RUN echo "http://mirror.leaseweb.com/alpine/v3.13/community" >> /etc/apk/repositories

RUN wget 'http://openresty.org/package/admin@openresty.com-5ea678a6.rsa.pub'
RUN mv 'admin@openresty.com-5ea678a6.rsa.pub' /etc/apk/keys/

# then, add the repo:
RUN . /etc/os-release
#RUN MAJOR_VER=`echo $VERSION_ID | sed 's/\.[0-9]\+$//'`

RUN echo "http://openresty.org/package/alpine/v3.13/main" \
    | tee -a /etc/apk/repositories

# update the local index cache:
RUN apk update

RUN apk add --no-cache --virtual .builddeps \
    openresty \
    openresty-openssl111-dev \
    automake \
    autoconf \
    libtool \
    pkgconfig \
    cmake \
    build-base \
    git \
    make \
    curl \
    openssl \
    wget \
    unzip 

# install LuaRocks
RUN curl https://raw.githubusercontent.com/apache/apisix/master/utils/linux-install-luarocks.sh -sL | bash 

RUN apk del .builddeps 
