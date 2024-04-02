FROM debian:12-slim AS build-env

ARG DEBCONF_NOWARNINGS yes

RUN apt-get update \
    && apt-get install --no-install-suggests --no-install-recommends --yes \
        sqlite3 \
    && apt-get -y clean

ENTRYPOINT ["/usr/bin/sqlite3"]
