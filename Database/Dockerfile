FROM node:alpine
RUN apt-get update && apt-get upgrade -y && apt-get install -y curl && apt-get clean
WORKDIR /app
COPY package*.json ./
RUN npm install --legacy-peer-deps
COPY . .
RUN apk add --no-cache curl
HEALTHCHECK --interval=10s --timeout=3s --retries=3 \
CMD curl --fail http://localhost:3000/healthz || exit 1
EXPOSE 3000
CMD ["node", "server.js"]
