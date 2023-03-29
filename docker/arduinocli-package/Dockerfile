FROM arduinoci/ci-arduino-cli:latest

# for esptool.py
RUN ln -s /usr/bin/python3 /usr/bin/python

ARG version
ARG core_args
ARG package
ARG platform
ARG build

RUN arduino-cli core $core_args update-index && \
    arduino-cli core $core_args install ${package}:${platform}@${version}
