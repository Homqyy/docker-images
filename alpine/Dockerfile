FROM alpine:3.20.3
ARG COUNTRY=

USER root

# if country is CN, replace the mirror
RUN if [ "$COUNTRY" = "CN" ]; then \
        wget -qO- https://raw.githubusercontent.com/Homqyy/china-mirror/main/os.sh | sh; \
            || { echo "Failed to replace mirror"; exit 1; }; \
    fi

# cleanup
RUN rm -rf china-mirror