FROM centos:centos7

ENV PORT=5555
ENV DEBIAN_FRONTEND=noninteractive

RUN yum -y install epel-release
RUN yum -y update && \
    yum clean all
RUN yum -y install vim
RUN yum -y install make gcc gcc-c++ autoconf cmake3 json-devel libusb-devel
RUN yum -y install automake git cmake
RUN yum -y install gdb
RUN yum -y install curl wget
RUN yum -y install centos-release-scl
RUN yum -y install devtoolset-7

# python stuff
RUN yum -y install zlib-devel bzip2 bzip2-devel readline-devel sqlite \
    sqlite-devel openssl-devel xz xz-devel libffi-devel
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
