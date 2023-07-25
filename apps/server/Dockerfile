# 设置 Node.js 版本
FROM node:16

# 安装 pnpm
RUN npm install -g pnpm

# 设置工作目录
WORKDIR /server

# 复制 package.json 和 pnpm-lock.yaml（如果有）来安装项目依赖
COPY package.json pnpm-lock.yaml ./

# 安装依赖
RUN pnpm install

# 将整个项目复制到容器中
COPY . .

# 安装 pm2
RUN npm install -g pm2

# 暴露 NestJS 默认端口
EXPOSE 3334

# 启动 NestJS 应用
CMD [ "pm2", "restart", "ecosystem.config.js" ]
