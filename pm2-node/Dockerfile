FROM node:22-alpine

ENV NODE_ENV=production

WORKDIR /usr/src/app

RUN npm install -g pm2

COPY package*.json ./
RUN npm ci --only=production

COPY . .

USER node

EXPOSE 3000

# Healthcheck: pm2 list returns 0 if app is up, else non-0 triggers container restart
HEALTHCHECK --interval=30s --timeout=10s --start-period=30s --retries=3 \
    CMD pm2 list | grep -q 'online' || exit 1

CMD ["pm2-runtime", "ecosystem.config.js"]
