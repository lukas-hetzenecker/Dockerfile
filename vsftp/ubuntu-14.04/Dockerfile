#++++++++++++++++++++++++++++++++++++++
# VSFTP Docker container
#++++++++++++++++++++++++++++++++++++++

FROM webdevops/base:latest
MAINTAINER info@webdevops.io
LABEL vendor=WebDevOps.io
LABEL io.webdevops.layout=4
LABEL io.webdevops.version=0.18.0

ENV FTP_USER     application
ENV FTP_PASSWORD application
ENV FTP_UID      1000
ENV FTP_GID      1000
ENV FTP_PASSWORD dev
ENV FTP_PATH     /data/ftp/

# Install vsftp
RUN /usr/local/bin/apt-install \
        vsftpd \
    && ln -sf /opt/docker/etc/vsftpd/vsftpd.conf /etc/vsftpd.conf \
    && mkdir -p \
            /var/run/vsftpd/empty \
            /var/log/supervisor

# Deploy scripts/configurations
COPY conf/ /opt/docker/
RUN /opt/docker/bin/control.sh provision.role webdevops-vsftp \
    && /opt/docker/bin/bootstrap.sh

EXPOSE 20
EXPOSE 21
EXPOSE 12020
EXPOSE 12021
EXPOSE 12022
EXPOSE 12023
EXPOSE 12024
EXPOSE 12025

CMD ["supervisord"]
