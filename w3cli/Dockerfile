FROM node:20 AS build-env
WORKDIR /opt/w3cli

RUN npm install @web3-storage/w3cli

FROM gcr.io/distroless/nodejs20-debian12
COPY --from=build-env /opt/w3cli /opt/w3cli
WORKDIR /opt/w3cli
ENTRYPOINT ["/nodejs/bin/node", "/opt/w3cli/node_modules/.bin/w3"]
CMD ["--help"]
