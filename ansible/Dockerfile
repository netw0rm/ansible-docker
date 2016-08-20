# Dockerfile for building Ansible image for Alpine, with as few additional software as possible.
#


# pull base image
FROM alpine:latest

MAINTAINER Shawn <qiusct@gmail.com>


RUN echo "===> Adding Python runtime..."  && \
    apk --update add python py-pip openssl ca-certificates  && \
    apk --update add --virtual build-dependencies build-base openssl-dev libffi-dev python-dev  && \
    pip install --upgrade pip    && \
    \
    \
    echo "===> Installing Ansible..."         && \
    pip install ansible pywinrm docker-py     && \
    \
    \
    echo "===> Removing package list..."  && \
    apk del build-dependencies build-base openssl-dev libffi-dev python-dev && \
    rm -rf /var/cache/apk/*               && \
    \
    \
    echo "===> Adding hosts for convenience..."  && \
    mkdir -p /etc/ansible                        && \
    echo 'localhost' > /etc/ansible/hosts


# default command: display Ansible version
CMD [ "ansible", "--vrsion" ]
