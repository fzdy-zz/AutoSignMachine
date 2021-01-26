FROM alpine:latest

ENV REPO_URL=https://github.com/lunnlew/AutoSignMachine.git

WORKDIR /AutoSignMachine/

RUN set -ex \
        && apk update && apk upgrade\
        && apk add --no-cache tzdata  git  nodejs  moreutils  npm curl jq \
        && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
        && echo "Asia/Shanghai" > /etc/timezone

RUN git clone ${REPO_URL} /AutoSignMachine \
        && cd /AutoSignMachine \
        && git checkout main \
        && mkdir logs \
        && npm install

RUN cp /AutoSignMachine/docker/entrypoint.sh / \
        && chmod +x /entrypoint.sh

WORKDIR /AutoSignMachine

ENTRYPOINT /entrypoint.sh
