ARG SENTRY_IMAGE
FROM ${SENTRY_IMAGE}

# Use Chinese PyPI mirror
RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

RUN pip install https://github.com/stayallive/sentry-nodestore-s3/archive/main.zip

COPY . /usr/src/sentry

RUN if [ -s /usr/src/sentry/enhance-image.sh ]; then \
    /usr/src/sentry/enhance-image.sh; \
    fi

RUN if [ -s /usr/src/sentry/requirements.txt ]; then \
    echo "sentry/requirements.txt is deprecated, use sentry/enhance-image.sh - see https://develop.sentry.dev/self-hosted/#enhance-sentry-image"; \
    pip install -r /usr/src/sentry/requirements.txt; \
    fi
