FROM alpine:3.9

ARG VERSION=2.23.4

ENV GHOST_NODE_VERSION_CHECK=false \
    NODE_ENV=production \
    GID=1000 UID=1000 \
    ADDRESS=https://my-ghost-blog.com
RUN mkdir /app

RUN apk -U upgrade \
 && apk add -t build-dependencies \
    python-dev \
    build-base \
 && apk add \
    bash \
	make \
    ca-certificates \
    grep \
    libressl \
    nodejs \
    nodejs-npm \
    python \
    s6 \
    su-exec \
    vim \
 && wget -q https://github.com/TryGhost/Ghost/releases/download/${VERSION}/Ghost-${VERSION}.zip -P /app \
 && unzip -q /app/Ghost-${VERSION}.zip -d /app \
 && npm install --development \
 && mv /app/content/themes/casper /app/casper \
 && apk del build-dependencies \
 && rm -rf /tmp/* /var/cache/apk/*

COPY rootfs /

RUN chmod +x /usr/local/bin/* /etc/s6.d/*/* /etc/s6.d/.s6-svscan/*

EXPOSE 2368

VOLUME /ghost/content

LABEL description="Ghost CMS ${VERSION}" \
      maintainer="Wonderfall <wonderfall@targaryen.house>"
WORKDIR /ghost
VOLUME /ghost
ENTRYPOINT ["run.sh"]
CMD ["/bin/s6-svscan", "/etc/s6.d"]
