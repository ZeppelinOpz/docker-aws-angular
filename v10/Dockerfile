FROM node:10

LABEL maintainer="ZeppelinOps"

RUN curl -sS http://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb http://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get -y upgrade
RUN apt-get -y install apt-utils
RUN apt-get -y install rsync yarn python-dev python-pip

RUN pip install awscli
RUN npm install -g @angular/cli

CMD bash