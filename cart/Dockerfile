FROM node:20 AS build
WORKDIR /app
COPY *.json .
COPY *.js .
RUN npm install

FROM node:20
WORKDIR /app
RUN addgroup roboshop && useradd -g roboshop roboshop && \
    chown -R roboshop:roboshop /app
ENV REDIS_HOST=redis \
    CATALOGUE_HOST=catalogue \
    CATALOGUE_PORT=8080
LABEL project="roboshop" \
      author="krishna" \
      component="cart"
COPY --chown=roboshop:roboshop --from=build /app /app
USER roboshop
CMD ["server.js"]
ENTRYPOINT ["node"]