FROM debian:jessie

ENV GLUSTER_VERSION 3.12
RUN apt update && apt install -y git make automake autoconf libtool flex bison pkg-config libssl-dev libxml2-dev python-dev libaio-dev libibverbs-dev librdmacm-dev libreadline-dev liblvm2-dev libglib2.0-dev liburcu-dev libcmocka-dev libsqlite3-dev libacl1-dev jq && git clone https://github.com/gluster/glusterfs.git && cd glusterfs &&  git checkout -b install remotes/origin/release-${GLUSTER_VERSION} && ./autogen.sh && ./configure && make && make install && ldconfig && rm -rf /var/lib/apt/lists/*
COPY storage /usr/bin/
COPY glusterfs/rancher-glusterfs common/* /usr/bin/
CMD ["start.sh", "storage", "--driver-name", "rancher-glusterfs"]
