# asign alias for multistage build
FROM --platform=$BUILDPLATFORM node:20-alpine as dependencies

WORKDIR /app

COPY package.json ./

RUN npm install


# asign alias for multistage build for test stage
FROM --platform=$BUILDPLATFORM node:20-alpine as tester

WORKDIR /app

COPY --from=dependencies /app/node_modules /app/node_modules

COPY . .

RUN npm run test

#dependencies productive stage
FROM --platform=$BUILDPLATFORM node:20-alpine as prodDependencies

WORKDIR /app

COPY package.json ./

RUN npm install --prod

#runner stage
FROM --platform=$BUILDPLATFORM node:20-alpine as runner

WORKDIR /app

COPY package.json ./

COPY --from=prodDependencies /app/node_modules /app/node_modules

COPY app.js ./

COPY tasks/ ./tasks

CMD ["npm", "start"]