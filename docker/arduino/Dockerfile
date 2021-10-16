FROM alpine:latest AS test

ARG version
ARG cli_version
ARG build

RUN test -n "$version"
RUN test -n "$cli_version"
RUN test -n "$build"

FROM debian:bullseye AS runtimebase

RUN apt-get update && \
    apt-get install -y openjdk-11-jre-headless python3 python3-serial git xz-utils unzip bzip2 cmake

FROM runtimebase AS buildbase

RUN apt-get update && \
    apt-get install -y git make gcc ant openjdk-11-jdk openjfx xz-utils unzip bzip2 xvfb

FROM buildbase AS cli

ARG cli_version

ADD arduino-cli-release /arduino-cli-release
RUN mkdir -p /cli-${cli_version} && \
    tar zxf arduino-cli-release/arduino-cli_*_Linux_64bit.tar.gz \
      -C /cli-${cli_version}

FROM buildbase AS build

ARG version

ADD arduino-release /arduino-release

RUN Xvfb :3 -nolisten tcp -screen :3 1280x800x24 & \
    xvfb="$!" && \
    export DISPLAY=:3 && \
    tar zxf arduino-release/source.tar.gz && \
    cd arduino-Arduino-*/build && \
    ant && \
    echo "skipping 'ant test', see issue [#1]" && \
    echo "$version" | ant dist && \
    xzcat linux/arduino-${version}-linux64.tar.xz|tar xC / && \
    kill -9 $xvfb

FROM runtimebase AS runtime

ARG version
ARG cli_version
ARG build

COPY --from=build /arduino-${version} /arduino-${version}
COPY --from=cli /cli-${cli_version} /cli-${cli_version}

RUN ln -s /arduino-${version}/arduino /usr/local/bin/arduino && \
    ln -s /cli-${cli_version}/arduino-cli /usr/local/bin/arduino-cli
