FROM node:16

LABEL "name"="dovbear"

ARG APP_DIR=/app

WORKDIR ${APP_DIR}

ADD . .

RUN npm i

ENV APP_PORT=3000 INSTANCE_NAME='dovbear' INSTANCE_HASH='somehash'
EXPOSE ${APP_PORT}

HEALTHCHECK --interval=10s --timeout=30s --start-period=5s --retries=3 CMD curl -s -f http://localhost:${APP_PORT}/healthz > /dev/null || exit 1

ENTRYPOINT ["node", "main.js"]