FROM nginx:stable-alpine-slim

LABEL maintainer="Thien Tran contact@tommytran.io"

RUN apk -U upgrade \
    && apk add ca-certificates libstdc++ \
    && update-ca-certificates \
    && rm -rf /var/cache/apk/*

COPY --from=ghcr.io/polarix-containers/hardened_malloc:2026081300 /install /usr/local/lib/
ENV LD_PRELOAD="/usr/local/lib/libhardened_malloc.so"