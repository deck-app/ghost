FROM ghost:5.12.0-alpine
LABEL maintainer Naba Das <hello@get-deck.com>
RUN apk update && \
    apk --no-cache add shadow sudo mysql-client
RUN usermod -u 501 node
COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh
RUN chmod +x /usr/local/bin/docker-entrypoint.sh
ENTRYPOINT [ "/usr/local/bin/docker-entrypoint.sh" ]