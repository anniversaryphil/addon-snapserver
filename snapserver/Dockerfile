ARG BUILD_FROM
FROM $BUILD_FROM

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# hadolint ignore=DL3003
RUN \
    apk add --no-cache \
        pulseaudio alsa-plugins-pulse bash \
    && rm -fr \
        /tmp/*
        
#Install Librespot - omitted as not using spotify
#RUN apk add --no-cache --repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing/ librespot=0.5.0-r0


#Install Snapcast - updated to current version as of 2024-11-08
RUN apk add --no-cache --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community/ snapcast-server=0.29.0-r0

#Install Snapweb correct version as of 2024-11-08
RUN \
    wget https://github.com/badaix/snapweb/releases/download/v0.8.0/snapweb.zip && \
    unzip -o snapweb.zip -d /usr/share/snapserver/snapweb/ && \
    rm snapweb.zip

# Copy data for add-on
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
