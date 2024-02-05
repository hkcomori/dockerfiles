FROM ghcr.io/hkcomori/github-cli:slim AS build-env

FROM debian:12-slim

ENV DEBCONF_NOWARNINGS=yes

RUN apt-get update \
    && apt-get install --no-install-suggests --no-install-recommends --yes \
        git ca-certificates \
    && apt-get -y clean

COPY --from=build-env \
    /usr/bin/gh \
    /usr/bin/

ENTRYPOINT ["/usr/bin/gh"]
CMD ["auth", "status"]
