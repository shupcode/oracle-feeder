FROM node:16-bullseye

RUN apt-get update && apt-get install -y aria2 lz4 vim
RUN groupadd -g ${UID} ${MONIKER} \
    && useradd -u ${UID} -g ${UID} -m ${MONIKER}
USER ${MONIKER}

WORKDIR /home/${MONIKER}/app

COPY --chown=${MONIKER}:${MONIKER} package*.json gate-api* ./

RUN npm i --production

COPY --chown=${MONIKER}:${MONIKER} tsconfig.json ./
COPY --chown=${MONIKER}:${MONIKER} src ./src
COPY --chown=${MONIKER}:${MONIKER} ./config/default.js ./config/default.js

EXPOSE 8532