# Dockerfile for building Ansible image for Alpine 3, with as few additional software as possible.
#
# Version  1.0
#


# pull base image
FROM alpine:latest

MAINTAINER Shawn <qiusct@gmail.com>


RUN echo "===> Adding Python runtime..."  && \
    apk --update add python py-pip openssl ca-certificates               && \
    apk --update add --virtual build-dependencies python-dev build-base  && \
    pip install --upgrade pip                                            && \
    \
    \
    echo "===> Installing Ansible..."  && \
    pip install ansible pywinrm        && \
    \
    \
    echo "===> Removing package list..."  && \
    apk del build-dependencies            && \
    rm -rf /var/cache/apk/*               && \
    \
    \
    echo "===> Adding hosts for convenience..."  && \
    mkdir -p /etc/ansible                        && \
    echo 'localhost' > /etc/ansible/hosts


# default command: display Ansible version
CMD [ "ansible-playbook", "--version" ]
