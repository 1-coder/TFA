# Use a stable, well-supported base image for our development environment.
# Ubuntu 20.04 LTS is a common choice for embedded toolchains.
FROM ubuntu:20.04

# Avoid interactive prompts during package installation.
ENV DEBIAN_FRONTEND=noninteractive

# Update package lists and install all necessary dependencies in a single layer to optimize image size.
RUN apt-get update && apt-get install -y --no-install-recommends \
    # Core build tools
    build-essential \
    git \
    make \
    cmake \
    # AArch64 cross-compiler toolchain for targeting Armv8-A
    gcc-aarch64-linux-gnu \
    g++-aarch64-linux-gnu \
    binutils-aarch64-linux-gnu \
    # QEMU system emulator for running the firmware on a virtual platform
    qemu-system-arm \
    # Dependencies required by the TF-A and U-Boot build systems
    python3 \
    python3-pip \
    bison \
    flex \
    device-tree-compiler \
    libssl-dev \
    # Clean up apt cache to reduce final image size
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Set the default working directory for the container.
# This is where your repository will be cloned.
WORKDIR /workspaces
