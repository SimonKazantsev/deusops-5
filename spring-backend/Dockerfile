FROM alpine AS builder

WORKDIR /app

RUN apk add maven --no-cache

COPY . .

RUN mvn package -DskipTests=true

FROM alpine

WORKDIR /app

RUN apk add openjdk21 --no-cache && \
    addgroup -S appuser && \
    adduser -S appuser -G appuser

USER appuser:appuser

COPY --from=builder /app/target/*.jar app.jar

CMD [ "java", "-jar", "app.jar" ] 