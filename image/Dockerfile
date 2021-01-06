### STAGE 1: Build ###
FROM ruby:alpine3.12 as base
LABEL maintainer="summer.gan@ringcentral.com"

# install node
ENV NODE_VERSION 11
RUN apk update \
    && apk add --no-cache yarn git bzip2 unzip nodejs=${NODE_VERSION} nodejs-npm alpine-sdk

# NPM install
RUN npm config set sass_binary_site https://npm.taobao.org/mirrors/node-sass/  \
  && npm config set registry https://registry.npm.taobao.org  \
  && npm cache clean --force

# Show version
RUN node --version \
    && npm version && git --version && ruby -v
    
# RUN apt-get install -y curl \
#   && curl -sL https://deb.nodesource.com/setup_${NODE_VERSION}.x | bash - \
#   && apt-get install -y nodejs \
#   && curl -L https://www.npmjs.com/install.sh | sh

# RUN npm install -g yarn \
#   && npm install -g @google/clasp

# # Show version
# RUN node --version \
#     && npm version && git --version && ruby -v