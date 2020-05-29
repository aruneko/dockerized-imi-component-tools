FROM node:14-alpine

ENV VERSON=1.0.0
ENV COMPONENT=imi-enrichment-hojin
ENV CONVERTER_VERSION=1.0.0
ENV CONV_COMPONENT=imi-moji-converter

WORKDIR /usr/local/${COMPONENT}

RUN apk --no-cache --virtual .build-deps add curl \
 && curl -o ${CONV_COMPONENT}-${CONVERTER_VERSION}.tgz \
    https://info.gbiz.go.jp/tools/imi_tools/resource/01/${CONV_COMPONENT}-${CONVERTER_VERSION}.tgz \
 && npm i ${CONV_COMPONENT}-${CONVERTER_VERSION}.tgz \
 && rm -rf ${CONV_COMPONENT}-${CONVERTER_VERSION}.tgz \
 && curl -o ${COMPONENT}-${VERSON}.tgz \
    https://info.gbiz.go.jp/tools/imi_tools/resource/01/${COMPONENT}-${VERSON}.tgz \
 && npm i ${COMPONENT}-${VERSON}.tgz \
 && rm -rf ${COMPONENT}-${VERSON}.tgz \
 && apk del .build-deps

EXPOSE 8080

CMD node /usr/local/${COMPONENT}/node_modules/${COMPONENT}/bin/server.js 8080
