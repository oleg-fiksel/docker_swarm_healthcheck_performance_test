FROM alpine:3.8

RUN apk --no-cache add curl \
    && curl -sL https://github.com/openfaas/faas/releases/download/0.9.14/fwatchdog > /usr/bin/fwatchdog \
    && chmod +x /usr/bin/fwatchdog

RUN apk add --no-cache figlet

# Populate example here
ENV fprocess="figlet"

#HEALTHCHECK --interval=5s CMD [ -e /tmp/.lock ] || exit 1
CMD ["fwatchdog"]

