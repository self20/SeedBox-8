FROM ubuntu:16.04
MAINTAINER AshDev <ashdevfr@gmail.com>

ENV DELUGE_VERSION 1.3.14
ENV DELUGE deluge-$DELUGE_VERSION
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
	apt-get install -y wget python python-twisted python-openssl python-setuptools intltool python-xdg python-chardet geoip-database python-libtorrent python-notify python-pygame python-glade2 librsvg2-common xdg-utils python-mako

#Build deluge from source
RUN wget http://download.deluge-torrent.org/source/$DELUGE.tar.gz -O /tmp/$DELUGE.tar.gz
RUN tar xvfz /tmp/$DELUGE.tar.gz -C /opt/
WORKDIR /opt/$DELUGE
RUN python setup.py build
RUN python setup.py install --install-layout=deb

EXPOSE 58846 8112 11886

CMD /usr/bin/deluged -c /mnt/config && /usr/bin/deluge-web -c /mnt/config
