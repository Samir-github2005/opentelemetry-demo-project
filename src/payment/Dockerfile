FROM node:22-alpine AS build
WORKDIR /usr/src/app
COPY ./src/payment/package*.json ./
RUN npm ci  --omit=dev


FROM node:22-alpine
WORKDIR /usr/src/app
ENV NODE_ENV=production
COPY --from=build /usr/src/app/node_modules ./node_modules
COPY ./src/payment/ ./
COPY ./pb/demo.proto ./

EXPOSE ${PAYMENT_PORT}
CMD ["npm","run","start"] 

