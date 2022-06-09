# 基于node14基础镜像
FROM node:14

#一些元数据，比如作者信息
LABEL maintainer="yangjiapei"

# 安装pm2
RUN npm install pm2 -g --registry=https://registry.npmmirror.com

# 暴露容器的端口
EXPOSE 80 443