FROM debian:trixie-slim

RUN apt-get update -y && \
    apt-get install wget p7zip -y

WORKDIR /app

ARG MONERO_WALLET_VERSION=0.18.4.5

RUN wget https://downloads.getmonero.org/cli/monero-linux-x64-v${MONERO_WALLET_VERSION}.tar.bz2 && \
    7z monero-linux-x64-v${MONERO_WALLET_VERSION}.tar.bz2 && \
    7z monero-linux-x64-v${MONERO_WALLET_VERSION}.tar && \
    rm -f monero-linux-x64-v${MONERO_WALLET_VERSION}.tar.bz2 && \
    rm -f monero-linux-x64-v${MONERO_WALLET_VERSION}.tar


COPY ./monerod.conf /etc/monerod.conf

EXPOSE 18080
EXPOSE 18081
EXPOSE 18083
EXPOSE 18089

CMD [ "monero-linux-x64-v${MONERO_WALLET_VERSION}/monerod", "--config-file", "/etc/monerod.conf" ]
