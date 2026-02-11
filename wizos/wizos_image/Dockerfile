FROM registry.os.wiz.io/python3:latest

# WIZOS_CLIENT secrets are passed to this dockerfile by `docker build`
# use apk-auth to install packages from the wizos apk registry
RUN --mount=type=secret,id=WIZOS_CLIENT_ID \
 --mount=type=secret,id=WIZOS_CLIENT_SECRET \
 export $(WIZOS_SECRET_PATH=/run/secrets apk-auth) && \
 apk add --no-cache \
 python3

WORKDIR /app

COPY ./src/ /app

ENTRYPOINT ["python3", "main.py"]
