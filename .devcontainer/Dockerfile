
# Updated for Debian base and TeX Live compatibility
FROM mcr.microsoft.com/devcontainers/base:debian

# Install dependencies
USER root
RUN apt-get update && apt-get install -y \
  perl \
  wget \
  xz-utils \
  tar \
  fontconfig \
  libfreetype6 \
  lua5.3 \
  gcc \
  texlive \
  texlive-latex-extra \
  texlive-fonts-recommended \
  texlive-fonts-extra \
  texlive-science \
  texlive-pictures \
  texlive-xetex \
  texlive-luatex \
  # texlive-math-extra (not available in Debian) \
  texlive-humanities \
  texlive-lang-all \
  dvisvgm \
  latexmk \
  && rm -rf /var/lib/apt/lists/*

# Switch back to vscode user
USER vscode

# Setup workdir
WORKDIR /home/vscode

# Verify latex and dvisvgm
RUN latex --version
RUN dvisvgm --version

# Setup test
RUN mkdir /tmp/test
WORKDIR /tmp/test
WORKDIR /home/vscode
