# ### STAGE 1: Build ###
# FROM ruby:alpine3.12 as base
# LABEL maintainer="summer.gan@ringcentral.com"

# # install node
# RUN apk update \
#     && apk add --no-cache yarn=1.21.1 git bzip2 unzip nodejs=10.19.0 nodejs-npm=10.19.0 alpine-sdk

# # NPM install
# RUN npm config set sass_binary_site https://npm.taobao.org/mirrors/node-sass/  \
#   && npm config set registry https://registry.npm.taobao.org  \
#   && npm cache clean --force
FROM node:20.12.0 AS nodejs

FROM ruby:2

ENV LANG C.UTF-8

ENV NODE_VERSION 20.12.0

# RUN groupadd --gid 1000 node \
#   && useradd --uid 1000 --gid node --shell /bin/bash --create-home node

COPY --from=nodejs /usr/local/bin/node /usr/local/bin/
COPY --from=nodejs /usr/local/lib/node_modules /usr/local/lib/node_modules
COPY --from=nodejs /opt/ /opt/

RUN ln -sf /usr/local/bin/node /usr/local/bin/nodejs \
  && ln -sf ../lib/node_modules/npm/bin/npm-cli.js /usr/local/bin/npm \
  && ln -sf ../lib/node_modules/npm/bin/npx-cli.js /usr/local/bin/npx \
  && ln -sf /opt/yarn*/bin/yarn /usr/local/bin/yarn \
  && ln -sf /opt/yarn*/bin/yarnpkg /usr/local/bin/yarnpkg
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