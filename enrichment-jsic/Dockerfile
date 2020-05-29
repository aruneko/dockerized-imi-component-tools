FROM node:14-alpine

ENV VERSON=1.0.0
ENV COMPONENT=imi-enrichment-jsic

WORKDIR /usr/local/${COMPONENT}

RUN apk --no-cache --virtual .build-deps add curl \
 && curl -o ${COMPONENT}-${VERSON}.tgz \
    https://info.gbiz.go.jp/tools/imi_tools/resource/${COMPONENT}/${COMPONENT}-${VERSON}.tgz \
 && npm i ${COMPONENT}-${VERSON}.tgz \
 && rm -rf ${COMPONENT}-${VERSON}.tgz \
 && apk del .build-deps

EXPOSE 8080

CMD node /usr/local/${COMPONENT}/node_modules/${COMPONENT}/bin/server.js 8080
