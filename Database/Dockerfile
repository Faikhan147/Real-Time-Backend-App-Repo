FROM node:alpine
RUN apk add --no-cache curl
WORKDIR /app
COPY package*.json ./
RUN npm install --legacy-peer-deps
COPY . .
RUN apk add --no-cache curl
HEALTHCHECK --interval=10s --timeout=3s --retries=3 \
CMD curl --fail http://localhost:3000/healthz || exit 1
EXPOSE 3000
CMD ["node", "server.js"]
