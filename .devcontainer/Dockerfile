# https://github.com/wadedos/alpine-tinytex/blob/master/Dockerfile

FROM mcr.microsoft.com/devcontainers/base:alpine

# tinytex dependencies
RUN apk --no-cache add \
  perl  \
  wget \
  xz \
  tar \
  fontconfig \
  freetype \
  lua \
  gcc

# install as vscode
USER vscode

# setup workdir
WORKDIR /home/vscode

# setup path
ENV PATH=/home/vscode/.TinyTeX/bin/x86_64-linuxmusl/:$PATH

# download and install tinytex
RUN wget -qO- "https://yihui.name/gh/tinytex/tools/install-unx.sh" | sh

# add tlmgr to path
RUN /home/vscode/.TinyTeX/bin/*/tlmgr path add

# verify latex version
RUN latex --version

# verify tlmgr version
RUN tlmgr --version

# install texlive packages
RUN tlmgr install \
    preview \
    standalone \
    dvisvgm \
    moderncv \
    colortbl \
    fontawesome5 \
    pgf \
    multirow \
    arydshln \
    academicons

# verify 
RUN dvisvgm --version

# setup test
RUN mkdir /tmp/test

# test workdir
WORKDIR /tmp/test

# reset workdir
WORKDIR /home/vscode