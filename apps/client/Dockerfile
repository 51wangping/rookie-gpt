# 设置 Node.js 版本
FROM node:16

# 安装 pnpm
RUN npm install -g pnpm

# 设置工作目录
WORKDIR /client

# 复制 package.json 和 pnpm-lock.yaml（如果有）来安装项目依赖
COPY package.json pnpm-lock.yaml ./

# 安装依赖
RUN pnpm install

# 将整个项目复制到容器中
COPY . .

# 构建 React 项目
RUN npm run build

# 使用 Nginx 作为 Web 服务器来托管 React 静态文件
FROM nginx:latest
COPY --from=0 /client/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
