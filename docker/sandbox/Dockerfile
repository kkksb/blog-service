FROM ubuntu:focal

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Azia/Tokyo

RUN \
    apt-get update -y && \
    apt-get install -y --no-install-recommends \
    curl \
    libnuma-dev \
    zlib1g-dev \
    libgmp-dev \
    libgmp10 \
    git \
    wget \
    lsb-release \
    software-properties-common \
    gnupg2 \
    apt-transport-https \
    gcc \
    autoconf \
    automake \
    build-essential

ARG GPG_KEY=7784930957807690A66EBDBE3786C5262ECB4A3F
RUN gpg --batch --keyserver keys.openpgp.org --recv-keys $GPG_KEY

RUN bash -c "curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | sh"
RUN bash -c "curl -sSL https://get.haskellstack.org/ | sh"

ENV PATH=${PATH}:/root/.local/bin
ENV PATH=${PATH}:/root/.ghcup/bin

ARG GHC=8.10.7
ARG CABAL=3.6.2.0
ARG STACK=2.7.5

RUN bash -c "ghcup upgrade"
RUN bash -c "ghcup install cabal $CABAL"
RUN bash -c "ghcup set cabal $CABAL"

RUN bash -c "ghcup install ghc $GHC"
RUN bash -c "ghcup set ghc $GHC"

RUN bash -c "ghcup install stack $STACK"
RUN bash -c "ghcup set stack $STACK"

RUN bash -c "echo PATH="$HOME/.local/bin:$PATH" >> $HOME/.bashrc"
RUN bash -c "echo export LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH" >> $HOME/.bashrc"
RUN bash -c "source $HOME/.bashrc"

RUN bash -c "stack install implicit-hie"