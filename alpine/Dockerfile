FROM alpine:3.20.3
ARG COUNTRY=

USER root

RUN apk add --no-cache git

# if country is CN, replace the mirror
RUN if [ "$COUNTRY" = "CN" ]; then \
        git clone https://github.com/Homqyy/china-mirror \
        && sh china-mirror/os.sh; \
    fi

# cleanup
RUN if [ "$COUNTRY" = "CN" ]; then \
        rm -rf china-mirror; \
    fi