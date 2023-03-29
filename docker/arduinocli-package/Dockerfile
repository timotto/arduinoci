FROM arduinoci/ci-arduino-cli:latest

ARG version
ARG core_args
ARG package
ARG platform

RUN arduino-cli core $core_args update-index && \
    arduino-cli core $core_args install ${package}:${platform}@${version}
