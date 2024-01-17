FROM debian:12-slim AS build-env

ENV DEBCONF_NOWARNINGS=yes

RUN apt-get update \
    && apt-get install --no-install-suggests --no-install-recommends --yes \
    privoxy \
    && apt-get -y clean

FROM gcr.io/distroless/static-debian12

# Copy privoxy files
COPY --from=build-env \
    /etc/privoxy/* \
    /etc/privoxy
COPY --from=build-env \
    /usr/sbin/privoxy \
    /usr/sbin/

# Copy dependencies inspected by `ldd /usr/sbin/privoxy`
COPY --from=build-env \
    /lib/x86_64-linux-gnu/libbrotlidec.so.1 \
    /lib/x86_64-linux-gnu/libmbedtls.so.14 \
    /lib/x86_64-linux-gnu/libmbedx509.so.1 \
    /lib/x86_64-linux-gnu/libmbedcrypto.so.7 \
    /lib/x86_64-linux-gnu/libz.so.1 \
    /lib/x86_64-linux-gnu/libpcre.so.3 \
    /lib/x86_64-linux-gnu/libpcreposix.so.3 \
    /lib/x86_64-linux-gnu/libc.so.6 \
    /lib/x86_64-linux-gnu/libbrotlicommon.so.1 \
    /lib/x86_64-linux-gnu/
COPY --from=build-env \
    /lib64/ld-linux-x86-64.so.2 \
    /lib64/

EXPOSE 8118

WORKDIR /etc/privoxy
ENTRYPOINT ["/usr/sbin/privoxy", "--no-daemon"]
CMD ["/etc/privoxy/config"]
