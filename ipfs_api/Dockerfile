FROM --platform=linux/amd64 python:3.10

COPY . /app

WORKDIR /tmp
RUN ["wget", "https://dist.ipfs.tech/kubo/v0.24.0/kubo_v0.24.0_linux-amd64.tar.gz"]
RUN ["tar", "-xvzf", "kubo_v0.24.0_linux-amd64.tar.gz"]
WORKDIR /tmp/kubo
RUN ["bash", "./install.sh"]
RUN ["ipfs", "init"]

WORKDIR /app
RUN ["pip3", "install", "-r", "requirements.txt"]

EXPOSE 4243
EXPOSE 5001
EXPOSE 8080
EXPOSE 4001

CMD ["sh", "-c", "uvicorn main:app --port ${IPFS_API_PORT:-4243} --host ${IPFS_API_HOST:-0.0.0.0} --reload"]








