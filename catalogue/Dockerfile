FROM node:20 AS build
WORKDIR /app
COPY *.json .
COPY *.js .
RUN npm isntall

FROM node:20
WORKDIR /app
RUN addgroup roboshop && useradd -g roboshop roboshop/
    chown -R roboshop:roboshop /app
ENV MONGO=true 
    MONGO_URL="mongodb://mongodb:27017/catalogue"
COPY --chown=roboshop:roboshop --from=build /app /app
USER roboshop
EXPOSE 8080
LABEL project="roboshop" \
      author="krishna" \
      component="catalogue" 
CMD ["server.js"]
ENTRYPOINT ["node"]