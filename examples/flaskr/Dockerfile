############################################################
# Dockerfile to build Flask App
# Based on
############################################################

# Set the base image
FROM ubuntu:16.04

# File Author / Maintainer
MAINTAINER Mill Chen

EXPOSE 5000
ENV FLASK_APP flaskr
ENV FLASK_DEBUG False
ENV LC_ALL C.UTF-8
ENV LANG C.UTF-8

# for development: keep vim
# for production: remove vim
RUN apt-get update \
 && apt-get install -y \
    curl \
    apache2 \
    libapache2-mod-wsgi \
    build-essential \
    python3 \
    python3-dev \
    python3-pip \
    vim \
 && apt-get clean \
 && apt-get autoremove \
 && rm -rf /var/lib/apt/lists/*

RUN pip3 install --upgrade pip
COPY . /root/flaskr/

WORKDIR /root/flaskr

RUN pip install --editable /root/flaskr/ 
RUN /usr/local/bin/flask initdb

CMD /usr/local/bin/flask run --host='0.0.0.0'
