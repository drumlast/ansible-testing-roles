FROM quay.io/centos/centos:8

# Переключаем репозитории на vault
RUN sed -i 's|mirrorlist=|#mirrorlist=|g' /etc/yum.repos.d/*.repo && \
    sed -i 's|#baseurl=http|baseurl=http|g' /etc/yum.repos.d/*.repo && \
    sed -i 's|mirror.centos.org|vault.centos.org|g' /etc/yum.repos.d/*.repo

# Базовые пакеты
RUN dnf install -y gcc openssl-devel bzip2-devel libffi-devel make wget tar \
    && dnf clean all

# Скачиваем и собираем Python 3.9
RUN cd /usr/src && \
    wget https://www.python.org/ftp/python/3.9.18/Python-3.9.18.tgz && \
    tar xzf Python-3.9.18.tgz && \
    cd Python-3.9.18 && \
    ./configure --enable-optimizations && \
    make altinstall

# Теперь python3.9 доступен как python3.9
RUN ln -s /usr/local/bin/python3.9 /usr/bin/python3.9 && \
    python3.9 -m ensurepip && \
    python3.9 -m pip install --upgrade pip setuptools wheel

# Ansible 2.14 + 2.15 + Molecule + Podman
RUN python3.9 -m pip install \
        ansible-core==2.14.7 \
        ansible==5 \
        molecule molecule_podman \
        selinux jmespath lxml

WORKDIR /opt/vector-role
CMD ["/bin/bash"]

