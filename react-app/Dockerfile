FROM node:14

#设置环境变量
ENV PROJECT_ENV production
ENV NODE_ENV production

RUN apt-get update && apt-get install -y nginx

COPY package*.json /app/

# 切换到app目录
WORKDIR /app

RUN npm install --registry=https://registry.npmmirror.com

COPY . /app

RUN npm run build

COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

# 启动 nginx ，关闭守护式运行，否则容器启动后会立刻关闭
CMD ["nginx", "-g", "daemon off;"]