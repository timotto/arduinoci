FROM debian:stable-slim

RUN apt-get update && apt-get install -y python3 python3-serial

ADD arduino-cli-release /arduino-cli-release

ARG cli_version

RUN mkdir -p /cli-${cli_version} && \
    tar zxf arduino-cli-release/arduino-cli_*_Linux_*.tar.gz \
      -C /cli-${cli_version} && \
    ln -s /cli-${cli_version}/arduino-cli /usr/local/bin/arduino-cli
