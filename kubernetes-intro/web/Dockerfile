FROM nginx:latest

RUN usermod -u 1001 nginx && groupmod -g 1001 nginx
COPY nginx.conf /etc/nginx/conf.d/default.conf

RUN mkdir /app && \
    chown -R nginx:nginx /app && \
    chmod -R 755 /app

COPY ./static/* /app
WORKDIR /app

EXPOSE 8000
CMD ["nginx", "-g", "daemon off;"]