# docker

 docker 本地从简单到实践的测试项目

  1. react-app

    前端单页面应用

    Dockerfile 生成的镜像像文件, 包含 node14 和 nginx 两个基础镜像;
    Dockerfile.multi ，多层构建，基础镜像 nginx:alpine, node:alpine 仅仅作为打包环境，整体的镜像体积减少；

  2. node-redis

     node 后端服务应用、docker 化

     涉及知识点：容器和容器之间的通信（ Networking ）

  3. my-all-app

    Docker compose

    把多个项目顺序启动

    ```
      # 启动所有容器
      docker-compose up -d
      # 停止所有容器
      docker-compose stop
    ```

  涉及到的 docker 命令

  ```
    // 构建镜像
    docker build -t yangjp/react-app:1.0 .

    // 启动容器 交互式启动，分配一个输入终端
    docker run -it --name my-app yangjp/react-app:1.0 /bin/bash

    // 后台启动容器 指定映射端口 
    docker run -d --name my-app -p 8888:80 yangjp/react-app

    // 在运行的容器中执行命令
    docker exec -it my-app /bin/bash

    // 查看已经在运行的容器
    docker ps -a

    // 创建一个app-test 网络
    docker network create app-test

    // 把需要通信的容器都加入到 app-test 网络里，之后容器间就可以互相访问了
    docker run -d --name redis-app --network app-test -p 6389:6379 redis
    docker run -it --name node-app --newwork app-test node:14 /bin/bash
  ```

  后续：
  * 使用 nginx 或者 traefik 做反向代理
  * 使用 kubernetes 或者 compose 等做编排
  * 使用 gitlab ci 或者 drone ci 等做 CI/CD