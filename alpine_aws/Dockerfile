FROM alpine:latest

RUN apk add --update --no-cache openssh 

RUN echo 'PasswordAuthentication yes' >> /etc/ssh/sshd_config

RUN adduser -h /home/remote_user -s /bin/sh -D remote_user

RUN echo -n 'remote_user:S@mpleP@ssword1' | chpasswd

RUN apk add --no-cache \
        python3 \
        py3-pip \
    && pip3 install --upgrade pip \
    && pip3 install --no-cache-dir \
        awscli \
    && rm -rf /var/cache/apk/*

RUN aws --version 

ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 22

COPY entrypoint.sh /

RUN chmod +x /entrypoint.sh
