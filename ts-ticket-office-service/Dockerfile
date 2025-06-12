FROM node:18-alpine

RUN apk add --no-cache tzdata \
 && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
 && echo 'Asia/Shanghai' > /etc/timezone

WORKDIR /app

# 先复制 package 文件
COPY package.json package-lock.json* ./

RUN npm install

# 复制剩余代码
COPY ./public ./public
COPY ./bin ./bin
COPY ./app.js ./

EXPOSE 16108

CMD ["npm", "start"]

