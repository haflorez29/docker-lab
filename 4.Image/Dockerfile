# FROM --platform=linux/arm64 node:20-alpine
# FROM 4 node:20-alpine
FROM --platform=$BUILDPLATFORM node:20-alpine
# node alpine tiene directory /app

WORKDIR /app

COPY package.json ./

RUN npm install

COPY . .
# ./ = /app

RUN npm run test

RUN rm -rf test && -rf node_modules

RUN npm install --prod

CMD ["npm", "start"]