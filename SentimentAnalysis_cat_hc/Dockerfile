FROM python:2.7-alpine

RUN pip install textblob && \
    python -m textblob.download_corpora

RUN apk --no-cache add curl \
    && curl -sL https://github.com/openfaas/faas/releases/download/0.9.14/fwatchdog > /usr/bin/fwatchdog \
    && chmod +x /usr/bin/fwatchdog

WORKDIR /root/

COPY handler.py .

ENV fprocess="python handler.py"

HEALTHCHECK --interval=5s CMD cat /tmp/.lock || exit 1

CMD ["fwatchdog"]

