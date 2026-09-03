FROM ubuntu:24.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential \
        gdb \
        cmake \
        ninja-build \
        clang \
        clang-format \
        valgrind \
        git \
        ca-certificates \
        locales \
    && locale-gen ja_JP.UTF-8 \
    && rm -rf /var/lib/apt/lists/*

ENV LANG=ja_JP.UTF-8
ENV LC_ALL=ja_JP.UTF-8

RUN useradd --create-home --shell /bin/bash vscode

USER vscode
WORKDIR /workspaces/training_c

CMD ["sleep", "infinity"]
