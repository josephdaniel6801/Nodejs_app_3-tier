FROM node:24 as BUILDER

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

FROM node:24-alpine as RUNNER

WORKDIR /app

COPY package.json .

RUN npm install -g vite

COPY --from=BUILDER /app/dist ./dist

EXPOSE 4173

CMD ["vite", "preview", "--host", "0.0.0.0", "--port", "4173"]

