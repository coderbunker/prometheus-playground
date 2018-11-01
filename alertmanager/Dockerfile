FROM ubuntu as build-deps
ENV VERSION="0.15.2"
WORKDIR /usr/src/app
RUN apt update && \
    apt install -y wget ca-certificates && \
    wget https://github.com/prometheus/alertmanager/releases/download/v0.15.2/alertmanager-${VERSION}.linux-amd64.tar.gz && \
    tar xzvf alertmanager-${VERSION}.linux-amd64.tar.gz --strip 1 && \
    mv /usr/src/app/alertmanager /bin

# FROM scratch
# WORKDIR /bin
# COPY --from=build-deps /usr/src/app/alertmanager /bin

COPY alertmanager.yml /etc/config.yml

EXPOSE 9093

ENTRYPOINT ["/bin/alertmanager"]

CMD ["--config.file=/etc/config.yml"]