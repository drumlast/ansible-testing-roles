FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# ---- Обновление базовых пакетов ----
RUN apt update && apt install -y \
    software-properties-common \
    ca-certificates \
    curl wget git sudo make gcc \
    python3.8 python3.8-dev python3.8-venv python3-pip

# ---- Подман: добавляем официальное PPA от Kubic ----
RUN . /etc/os-release \
    && echo "deb https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_${VERSION_ID}/ /" \
       > /etc/apt/sources.list.d/devel:kubic:libcontainers:stable.list \
    && curl -L "https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/xUbuntu_${VERSION_ID}/Release.key" \
       | apt-key add - \
    && apt update \
    && apt install -y podman

# ---- Python → по умолчанию сделать 3.8 ----
RUN update-alternatives --install /usr/bin/python python /usr/bin/python3.8 1

# ---- Обновить PIP ----
RUN python -m pip install --upgrade pip setuptools wheel

# ---- Ansible + Molecule ----
RUN python -m pip install \
    ansible-core==2.12.10 \
    molecule==3.5.2 \
    molecule_podman \
    selinux \
    jmespath \
    lxml

# ---- Установка TOX ----
RUN python3.8 -m pip install tox

WORKDIR /opt/vector-role
CMD ["/bin/bash"]
