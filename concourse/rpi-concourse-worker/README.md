# Raspberry Pi Concourse Worker

This is a Docker image with a Houdini Concourse worker for Raspberry Pi.

## Using the Concourse Worker

Because it is a Houdini worker it runs pipeline tasks within the host environment instead of isolated Docker containers. I got stuck getting `containerd` running. I believe the default Raspian Linux Kernel is missing some options required for `containerd`.

Without the isolation of Docker containers, tasks have unhindered access to all hardware available to the Houdini Concourse worker. This makes it easy to forward the `/dev/ttyUSB0` device of an Arduino connected to the host into the container running the Concourse Worker.

Without the flexibility of Docker containers, tasks rely on the host system for tools and programs to be available. For this reason the `Dockerfile` has build arguments allowing to install additional packages.
