FROM ubuntu:22.04

RUN apt-get update && \
    apt-get install -y \
    ansible \
    python3 \
    ssh \
    sudo && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /ansible
COPY . .

CMD ["sleep", "infinity"]