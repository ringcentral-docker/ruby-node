### STAGE 1: Build ###
FROM ruby:alpine3.8 as base
LABEL maintainer="summer.gan@ringcentral.com"

# install node
ENV NODE_VERSION 11
RUN apt-get install -y curl \
  && curl -sL https://deb.nodesource.com/setup_${NODE_VERSION}.x | bash - \
  && apt-get install -y nodejs \
  && curl -L https://www.npmjs.com/install.sh | sh

RUN npm install -g yarn \
  && npm install -g @google/clasp

# Show version
RUN node --version \
    && npm version && git --version && ruby -v