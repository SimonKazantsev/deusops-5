FROM alpine

WORKDIR /app

EXPOSE 3000

RUN apk add npm --no-cache && \
    addgroup -S appuser && \
    adduser -S appuser -G appuser
    
COPY package.json package.json

RUN npm install --force --legacy-peer-deps && \
    chown -R appuser:appuser /app

USER appuser:appuser

COPY src /app/src
COPY public /app/public

CMD [ "npm", "start" ]