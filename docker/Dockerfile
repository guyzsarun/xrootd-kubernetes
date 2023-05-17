FROM opensciencegrid/software-base:3.6-el8-release
ARG  XROOTD_VERSION=5.5.4-1.1

LABEL org.opencontainers.image.source https://github.com/guyzsarun/xrootd-kubernetes

ARG UNAME=xrootd
ARG UID=492
ARG GID=493
RUN groupadd -g $GID -o $UNAME
RUN useradd -m -u $UID -g $GID -o -s /bin/bash $UNAME

RUN yum install -y  python3-scitokens \
                    xrootd-scitokens \
                    gfal2-plugin-xrootd \
                    xrootd-multiuser \
                    xrootd-lcmaps \
                    xrootd-client-compat \
                    xrootd-client \
                    scitokens-cpp

RUN yum install -y  xrootd-1:$XROOTD_VERSION.osg36.el8

RUN yum install -y xrootd-cmstfc --enablerepo=osg-contrib && yum clean all && rm -rf /var/cache/yum
RUN openssl rand -base64 -out /etc/xrootd/macaroon-secret 64

COPY xrootd /etc/xrootd/

ENTRYPOINT xrootd -c /etc/xrootd/xrootd-cluster.conf -d
