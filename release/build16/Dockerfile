FROM ubuntu:16.04
MAINTAINER Andy Wick <andy.wick@oath.com>

RUN apt-get update && \
apt-get install -y ruby-dev make python3-pip git libtest-differences-perl sudo wget libjson-pp-perl tzdata wget lsb-release && \
(cd /tmp; wget https://packages.ntop.org/apt-stable/16.04/all/apt-ntop-stable.deb; dpkg -i apt-ntop-stable.deb) && \
apt-get update && \
apt-get install -y pfring && \
apt-get -f install && \
gem install --no-ri --no-rdoc fpm; \
pip3 install awscli; \
useradd -u 2000 elasticsearch; \
(cd / ; \
 wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.5.1-linux-x86_64.tar.gz; \
 tar xf elasticsearch-7.5.1-linux-x86_64.tar.gz; \
 chown -R elasticsearch elasticsearch-7.5.1; \
 rm -f elasticsearch-7.5.1-linux-x86_64.tar.gz \
) && \
git clone https://github.com/aol/moloch && \
(cd moloch; git checkout master; ./easybutton-build.sh --daq --pfring) && \
mv moloch/thirdparty / && \
rm -rf /thirdparty/glib*/*/tests /thirdparty/glib*/*/*/tests && \
rm -rf moloch && \
rm -rf /var/lib/apt/lists/*
