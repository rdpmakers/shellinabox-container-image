FROM ubuntu:jammy

ENV SIAB_USERCSS="Normal:+/etc/shellinabox/options-enabled/00+Black-on-White.css,Reverse:-/etc/shellinabox/options-enabled/00_White-On-Black.css;Colors:+/etc/shellinabox/options-enabled/01+Color-Terminal.css,Monochrome:-/etc/shellinabox/options-enabled/01_Monochrome.css" \
    SIAB_PORT=4200 \
    SIAB_ADDUSER=true \
    SIAB_USER=webuser \
    SIAB_USERID=5000 \
    SIAB_GROUP=webuser \
    SIAB_GROUPID=5000 \
    SIAB_PASSWORD=W3BU23R \
    SIAB_SHELL=/bin/bash \
    SIAB_HOME=/home/guest \
    SIAB_SUDO=true \
    SIAB_SSL=false \
    SIAB_SERVICE=/:LOGIN \
    SIAB_PKGS=none \
    SIAB_SCRIPT=none

RUN apt-get update && apt-get install -y openssh-server passwd sysvinit-utils software-properties-common python3-pip wget git openssl screen lsb-release neofetch ca-certificates curl openssh-client sudo shellinabox && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    ln -sf '/etc/shellinabox/options-enabled/00+Black on White.css' \
      /etc/shellinabox/options-enabled/00+Black-on-White.css && \
    ln -sf '/etc/shellinabox/options-enabled/00_White On Black.css' \
      /etc/shellinabox/options-enabled/00_White-On-Black.css && \
    ln -sf '/etc/shellinabox/options-enabled/01+Color Terminal.css' \
      /etc/shellinabox/options-enabled/01+Color-Terminal.css

RUN echo "root:w3b2h3ll" | chpasswd

RUN mkdir -p /run/sshd

RUN echo "PermitRootLogin yes" >> /etc/ssh/sshd_config && \
    echo "PasswordAuthentication yes" >> /etc/ssh/sshd_config

EXPOSE 4200

VOLUME /etc/shellinabox /var/log/supervisor /home

ADD assets/entrypoint.sh /usr/local/sbin/

ENTRYPOINT ["entrypoint.sh"]
CMD ["shellinabox"]
