FROM        centos:7
MAINTAINER  Sandeep Kumar Singh <sandeepsingh4997@gmail.com>

ENV ALERT_MANAGER_VERSION=0.13.0

RUN yum -y update && yum -y upgrade  && \
    yum -y clean all && \
    curl -L -o /tmp/alert_manager.tar.gz https://github.com/prometheus/alertmanager/releases/download/v$ALERT_MANAGER_VERSION/alertmanager-$ALERT_MANAGER_VERSION.linux-amd64.tar.gz && \
    tar -xzf /tmp/alert_manager.tar.gz && \
    mv ./alertmanager-$ALERT_MANAGER_VERSION.linux-amd64/alertmanager /bin && \
    rm -rf ./alertmanager-$ALERT_MANAGER_VERSION.linux-amd64 && \
    rm /tmp/alert_manager.tar.gz

COPY config.yml /etc/alertmanager/config.yml

EXPOSE      9093
USER        nobody
VOLUME     [ "/alertmanager" ]
WORKDIR    /alertmanager
ENTRYPOINT [ "/bin/alertmanager" ]
CMD        [ "-config.file=/etc/alertmanager/config.yml", \
             "-storage.path=/alertmanager" ]
