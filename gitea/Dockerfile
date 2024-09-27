FROM gitea/gitea:1.21.11-rootless
ARG COUNTRY=

USER root

# if country is CN, replace the mirror
RUN if [ "$COUNTRY" = "CN" ]; then \
        git clone https://github.com/Homqyy/china-mirror \
        && sh china-mirror/os.sh; \
    fi

# Basic: refers to https://docs.gitea.com/administration/external-renderers
RUN apk --no-cache add asciidoctor freetype freetype-dev gcc g++ libpng libffi-dev py-pip python3-dev py3-pip py3-pyzmq

# if country is CN, replace the pip mirror
RUN if [ "$COUNTRY" = "CN" ]; then \
        bash china-mirror/pypi.sh; \
    fi

# Basic: refers to https://docs.gitea.com/administration/external-renderers
RUN pip3 install --upgrade pip
RUN pip3 install -U setuptools
RUN pip3 install jupyter docutils

# Support .ipynb
RUN pip3 install nbconvert

# cleanup
RUN rm -rf china-mirror

USER 1000:1000