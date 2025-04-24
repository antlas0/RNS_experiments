FROM python:3.11-bookworm

RUN apt-get update \
    && apt-get install -y sudo python3-pip build-essential \
    && apt-get clean \ 
    && rm -rf /var/lib/apt/lists/*

RUN useradd -ms /bin/bash runner
RUN usermod -aG sudo runner

WORKDIR /home/runner
USER runner

RUN python -m venv --copies .venv
ENV PATH="/home/runner/.venv:$PATH"
RUN python3 -m pip install rns

