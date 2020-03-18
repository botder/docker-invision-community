FROM nginx:1.17-alpine

COPY nginx.conf /etc/nginx/nginx.conf

# Setup permissions
ARG UID
ARG GID

RUN apk --no-cache add shadow \
    && usermod -u ${UID} nginx \
    && groupmod -g ${GID} nginx \
    && mkdir -p /var/www \
    && chown -R nginx:nginx /var/www /var/log/nginx /etc/nginx/nginx.conf

EXPOSE 8080
USER ${UID}:${GID}
CMD ["nginx", "-g", "daemon off;"]
