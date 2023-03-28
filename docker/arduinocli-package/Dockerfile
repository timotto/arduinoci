FROM arduinoci/ci-arduino-cli:latest

# for esptool.py
RUN ln -s /usr/bin/python3 /usr/bin/python

ARG version
ARG board_manager_url
ARG package
ARG platform
ARG build

RUN arduino-cli core --additional-urls ${board_manager_url} update-index && \
    arduino-cli core --additional-urls ${board_manager_url} install ${package}:${platform}@${version}
