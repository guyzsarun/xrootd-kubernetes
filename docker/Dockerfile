FROM opensciencegrid/software-base:3.6-el8-release

LABEL org.opencontainers.image.source https://github.com/guyzsarun/xrootd-kubernetes

ARG UNAME=xrootd
ARG UID=492
ARG GID=493
RUN groupadd -g $GID -o $UNAME
RUN useradd -m -u $UID -g $GID -o -s /bin/bash $UNAME

RUN yum -y install  osg-xrootd \
                    xrootd  \
                    xrootd-server \
                    xrootd-libs \
                    xrootd-server-libs \
                    xrootd-client \
                    xrootd-client-libs \
                    xrootd-scitokens \
                    python3-scitokens \
                    gfal2-plugin-xrootd \
                    xrootd-multiuser \
                    xrootd-lcmaps \
                    xrootd-client-compat \
                    xrootd-voms \
                    scitokens-cpp

RUN yum install -y xrootd-cmstfc --enablerepo=osg-contrib && yum clean all && rm -rf /var/cache/yum

COPY xrootd /etc/xrootd/

ENTRYPOINT xrootd -c /etc/xrootd/xrootd-cluster.conf -d
