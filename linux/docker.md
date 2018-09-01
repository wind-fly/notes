<!-- TOC -->

- [基本命令](#基本命令)
- [Container](#container)
- [构建镜像](#构建镜像)

<!-- /TOC -->


## 基本命令
``` bash

# 入门文章http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html

docker info
docker version

docker --version
docker run hello-world
docker run -d -p 80:80 --name webserver nginx
docker container ls # docker ps -a
docker container stop webserver
docker container ls -a
docker container rm webserver
docker image ls
docker image rm nginx

docker images
docker ps -a
docker kill
docker rm -f
docker rmi

# 这跟在本地直接执行 /bin/echo 'hello world' 几乎感觉不出任何区别
docker run ubuntu:14.04 /bin/echo 'Hello world'

# 下面的命令则启动一个 bash 终端，允许用户进行交互
# -t 选项让Docker分配一个伪终端（pseudo-tty）并绑定到容器的标准输入上
# -i 则让容器的标准输入保持打开
docker run -t -i ubuntu:14.04 /bin/bash

docker pull centos:latest

```

## Container
``` bash

# 新建容器，每运行一次，就会新建一个容器。同样的命令运行两次就，会生成两个一模一样的容器文件。如果希望重复使用容器，就要使用docker container start命令，它用来启动已经生成、已经停止运行的容器文件。
docker container start [containerID]


# docker container kill命令终止容器运行，相当于向容器里面的主进程发出 SIGKILL信号。而docker container stop命令也是用来终止容器运行，相当于向容器里面的主进程发出SIGTERM信号，然后过一段时间再发出 SIGKILL 信号。这两个信号的差别是，应用程序收到SIGTERM信号以后，可以自行进行收尾清理工作，但也可以不理会这个信号。如果收到SIGKILL信号，就会强行立即终止，那些正在进行中的操作会全部丢失。
docker container stop [containerID]


# 用来查看docker容器的输出，即容器里面Shell的标准输出。如果docker run命令运行容器的时候，没有使用-it参数，就要用这个命令查看输出。
docker container logs [containerID]


# 用于进入一个正在运行的docker容器。如果docker run命令运行容器的时候，没有使用-it参数，就要用这个命令进入容器。一旦进入了容器，就可以在容器的 Shell 执行命令了。
docker container exec -it [containerID] /bin/bash


# 用于从正在运行的Docker容器里面，将文件拷贝到本机。下面是拷贝到当前目录的写法。
docker container cp [containID]:[/path/to/file] ./

```

## 构建镜像
``` bash
docker image build -t koa-demo:0.0.1 .
```