FROM ghost:5.12.0-alpine
LABEL maintainer Naba Das <hello@get-deck.com>
RUN apk update && \
    apk --no-cache add shadow sudo
RUN usermod -u 501 node
COPY ./wait-for-it.sh /usr/local/bin/wait-for-it.sh