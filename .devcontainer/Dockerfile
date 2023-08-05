// https://github.com/wadedos/alpine-tinytex/blob/master/Dockerfile

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

# add user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# install as appuser
USER appuser

# setup workdir
WORKDIR /home/appuser

# setup path
ENV PATH=/home/appuser/.TinyTeX/bin/x86_64-linuxmusl/:$PATH

# download and install tinytex
RUN wget -qO- "https://yihui.name/gh/tinytex/tools/install-unx.sh" | sh

# add tlmgr to path
RUN /home/appuser/.TinyTeX/bin/*/tlmgr path add

# verify latex version
RUN latex --version

# verify tlmgr version
RUN tlmgr --version

# install texlive packages
RUN tlmgr install \
    preview \
    standalone \
    dvisvgm

# verify 
RUN dvisvgm --version

# setup test
RUN mkdir /tmp/test

# test workdir
WORKDIR /tmp/test

# copy test latex standalone equation
COPY ./test.tex .

# temp assign root to clean up tlmgr only dependencies
USER root

# remove dependencies
RUN apk del wget xz tar

# reset user
USER appuser

# run latex - ignore latex errors
RUN latex -interaction=nonstopmode  ./test.tex || true

# run dvisvgm with no-fonts
RUN dvisvgm --no-fonts ./test.dvi

# verify no-font svg was generated
RUN test -f test.svg

# remove no-font svg
RUN rm test.svg

# run dvisvgm with ttf font
RUN dvisvgm --font-format=ttf ./test.dvi

# verify ttf font svg was generated
RUN test -f test.svg

# clean up tests
RUN rm -R /tmp/*

# reset workdir
WORKDIR /home/appuser