FROM nginx
RUN rm -rf /usr/share/nginx/html/* && \
    rm -rf /etc/nginx/conf.d/default.conf \
    rm -rf /etc/nginx/nginx.conf
COPY nginx.conf /etc/nginx/nginx.conf
COPY static/ /usr/share/nginx/html/
# CMD ["nginx", "-g", "daemon off;"]