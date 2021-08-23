FROM --platform=linux/x86_64 ghost:3.40.2

LABEL MAINTAINER Naba Das <hello@get-deck.com>

RUN apt-get update -y && \
    apt-get install -y default-mysql-client
COPY ./wait-for-it.sh /usr/local/bin/wait-for-it.sh
RUN chmod +x /usr/local/bin/wait-for-it.sh
