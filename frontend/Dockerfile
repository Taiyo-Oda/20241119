# ベースイメージ
FROM node:18-alpine AS build-stage

# 作業ディレクトリ
WORKDIR /app

# パッケージ情報をコピーして依存関係をインストール
COPY package.json package-lock.json ./
RUN npm install

# アプリケーションをビルド
COPY . .
RUN npm run build

# 静的ファイルをNginxで提供
FROM nginx:alpine
COPY --from=build-stage /app/dist /usr/share/nginx/html