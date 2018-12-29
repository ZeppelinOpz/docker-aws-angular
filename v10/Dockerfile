FROM node:10-jessie-slim

LABEL maintainer="ZeppelinOps"

RUN apt-get update
RUN apt-get -y install apt-utils gettext-base
RUN apt-get -y install python-dev python-pip

RUN pip install awscli
RUN npm install -g @angular/cli

CMD bash
