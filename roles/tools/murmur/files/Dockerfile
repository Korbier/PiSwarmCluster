FROM alpine:3.8

RUN mkdir -pv /etc/murmur && apk add icu-dev murmur
EXPOSE 64738

RUN adduser -DHs /sbin/nologin mumble

USER mumble
VOLUME /etc/murmur
ENTRYPOINT ["murmurd","-fg","-ini","/etc/murmur/mumble-server.ini"]