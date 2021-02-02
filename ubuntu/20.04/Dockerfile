FROM ubuntu:20.04

ENV PORT=5555
ENV DEBIAN_FRONTEND=noninteractive

RUN apt update
RUN apt-get -y install git
RUN apt-get -y install vim
RUN apt -y install build-essential
RUN apt-get -y install manpages-dev
RUN apt-get -y install cmake
RUN apt-get -y install tzdata
RUN apt-get install -y gdb
RUN apt-get -y install wget
RUN apt-get -y install -y make build-essential libssl-dev zlib1g-dev \
    libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev \
    libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl
RUN apt-get -y install curl
RUN curl https://pyenv.run | bash
RUN echo 'export PATH="$HOME/.pyenv/bin:$PATH"' >> ~/.bashrc
RUN echo 'eval "$(pyenv init -)"' >> ~/.bashrc
ENV PATH="/root/.pyenv/bin:${PATH}"
RUN eval "$(pyenv init -)"
RUN pyenv install 3.9.1
RUN pyenv global 3.9.1
RUN pyenv versions
RUN eval "$(pyenv init -)"
RUN /root/.pyenv/shims/python3.9 -m pip install --upgrade pip setuptools wheel
RUN /root/.pyenv/shims/python3.9 -m pip install gdbgui
RUN /root/.pyenv/shims/python3.9 -m pip install pygdbmi
RUN /root/.pyenv/shims/python3.9 -m pip install gdbgui==0.13.2.0
RUN /root/.pyenv/shims/python3.9 -m pip install pygdbmi==0.9.0.0
RUN echo "set startup-with-shell off" >> ~/.gdbinit
COPY .vimrc /root/
COPY .vim /root/.vim
ENV PURE_PYTHON=1

EXPOSE ${PORT}
