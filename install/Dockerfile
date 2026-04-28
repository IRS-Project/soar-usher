# ============================
# SOAR USHER DOCKER IMAGE
# ============================
FROM python:3.10-slim-bookworm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    python3-dev \
    git \
    wget \
    ca-certificates \
    sudo

WORKDIR /HOME
RUN git clone https://github.com/IRS-Project/soar-usher.git
WORKDIR soar-usher
RUN ./install/installUbuntu.sh

WORKDIR /HOME/soar-usher/build
RUN wget http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/faSomeRecords \
    && wget http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/faSize \
    && chmod +x faSomeRecords faSize

RUN wget -q "https://github.com/nextstrain/nextclade/releases/download/v3.21.1/nextclade-x86_64-unknown-linux-musl" \
    -O /HOME/soar-usher/build/nextclade \
    && chmod +x /HOME/soar-usher/build/nextclade

ENV PATH="/HOME/soar-usher/build:${PATH}"
