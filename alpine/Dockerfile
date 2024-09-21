FROM alpine:3.20.3
ARG COUNTRY=

USER root

# if country is CN, replace the mirror
RUN if [ "$COUNTRY" = "CN" ]; then \
        curl -sSL https://raw.githubusercontent.com/Homqyy/china-mirror/main/os.sh | sh; \
    fi

# cleanup
RUN rm -rf china-mirror