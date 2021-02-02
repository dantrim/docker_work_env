# docker_work_env
Work (linux) docker environments

## Ubuntu:20.04

Dockerfile configuration located in [ubuntu/20.04/Dockerfile](ubuntu/20.04/Dockerfile).
Installs a C++ (GCC 9) and Python (3.9.1/pyenv) environment with `gdb` and `gdbgui` support.

### Example Run
```
docker pull dantrim/ubuntu:20.04
docker run -v ${PWD}:/home -p 5555:5555 -it dantrim/ubuntu:20.04 /bin/bash
# do stuff
# run gdbgui that can be accessed from host browser
{docker} gdbgui -n -p 5555 --host 172.17.0.2
```
