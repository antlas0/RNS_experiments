FROM python:3.11-bookworm

RUN apt-get update \
    && apt-get install -y sudo pipx build-essential \
    && apt-get clean \ 
    && rm -rf /var/lib/apt/lists/*

RUN useradd -ms /bin/bash runner
RUN usermod -aG sudo runner

COPY --chmod 0755 entrypoint.sh /entrypoint.sh

USER runner
WORKDIR /home/runner

RUN mkdir -p .reticulum/interfaces
COPY config.interface .reticulum/interfaces/config.interface

RUN python -m venv --copies .venv
ENV PATH="/home/runner/.venv:$PATH"
RUN python3 -m pipx ensurepath \
    && python3 -m pipx install rns

ENTRYPOINT ["/entrypoint.sh"]
