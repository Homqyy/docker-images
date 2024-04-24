FROM gitea/gitea:1.21.11-rootless
ARG COUNTRY=

USER root

# if country is CN, replace the mirror
RUN if [ "$COUNTRY" = "CN" ]; then \
        git clone https://github.com/Homqyy/china-mirror \
        && sh china-mirror/os.sh; \
    fi

# Support .ipynb
RUN apk add --no-cache python3 py3-pip

# if country is CN, replace the pip mirror
RUN if [ "$COUNTRY" = "CN" ]; then \
        sh china-mirror/pypi.sh; \
    fi

RUN pip3 install nbconvert

# cleanup
RUN rm -rf china-mirror

USER 1000:1000