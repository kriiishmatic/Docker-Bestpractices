FROM node:20 AS build
WORKDIR /app
COPY *.json .
COPY *.js .
RUN npm install

FROM node:20
WORKDIR /app
RUN addgroup roboshop && useradd -g roboshop roboshop && \
    chown -R roboshop:roboshop /app
ENV MONGO=true \
    REDIS_URL='redis://redis:6379' \
    MONGO_URL="mongodb://<MONGODB-SERVER-IP-ADDRESS>:27017/users" 
LABEL project="roboshop" \
      author="krishna" \
      component="user"
COPY --chown=roboshop:roboshop --from=build /app /app
USER roboshop
CMD ["server.js"]
ENTRYPOINT ["node"]
