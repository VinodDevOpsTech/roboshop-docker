FROM node:20.20.2-alpine3.22 AS builder
WORKDIR /app
COPY *.json .
COPY *.js .
RUN npm install


FROM node:20.20.2-alpine3.22
WORKDIR /app
EXPOSE "8080"
RUN addgroup -S roboshop && adduser -S -G appgroup roboshop && \
    chown -R roboshop:roboshop /app
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
COPY --from=builder /app /app
USER roboshop
CMD ["node", "server.js"]