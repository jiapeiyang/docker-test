FROM node:14

COPY package*.json /app/
WORKDIR /app
RUN npm install --registry=https://registry.npmmirror.com
COPY . /app
EXPOSE 3000
CMD ["node", "index.js"]