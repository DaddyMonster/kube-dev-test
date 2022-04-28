FROM node:lts-alpine as builder
RUN apk --no-cache add --virtual .builds-deps build-base python3

WORKDIR /app/builder

COPY package*.json yarn.* ./

RUN yarn install

FROM node:lts-alpine as base

ARG NODE_ENV
ARG BUILD_FLAG

WORKDIR /app/base

COPY --from=builder /app/builder/node_modules ./node_modules

COPY . .
