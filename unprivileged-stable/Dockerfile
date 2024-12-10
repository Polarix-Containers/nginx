FROM ghcr.io/nginxinc/nginx-unprivileged:stable-alpine

LABEL maintainer="Thien Tran contact@tommytran.io"

USER root

RUN apk -U upgrade \
    && apk add ca-certificates libstdc++ \
    && update-ca-certificates \
    && rm -rf /var/cache/apk/*

COPY --from=ghcr.io/polarix-containers/hardened_malloc:latest /install /usr/local/lib/
ENV LD_PRELOAD="/usr/local/lib/libhardened_malloc.so"

USER $UID