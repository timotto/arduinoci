FROM alpine:3.19

ARG extra_packages
RUN apk update && apk add bash curl jq ${extra_packages}

ARG extra_run=true
RUN ${extra_run}

ADD concourse-linux-arm64 /concourse

VOLUME /keys

VOLUME /work-dir

ENV CONCOURSE_WORK_DIR /work-dir

ENV CONCOURSE_TSA_WORKER_PRIVATE_KEY /keys/tsa_worker_private_key
ENV CONCOURSE_TSA_PUBLIC_KEY /keys/tsa_public_key
ENV CONCOURSE_TSA_HOST ""

ENV CONCOURSE_RUNTIME "houdini"

ENTRYPOINT ["/concourse", "worker"]
