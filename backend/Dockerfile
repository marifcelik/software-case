FROM node:19.7-alpine as builder
RUN npm install -g pnpm
RUN pnpm config set enable-pre-post-scripts true
WORKDIR /app
COPY ["package.json", "pnpm-lock.yaml", "./"]
RUN pnpm i
COPY . .
RUN pnpm build
RUN rm -rf src \
    tsconfig.json \
    README.md

EXPOSE 5048

CMD [ "pnpm", "start" ]