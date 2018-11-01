FROM ubuntu as build-deps
ENV VERSION="0.12.0"
WORKDIR /usr/src/app
RUN apt update && \
    apt install -y wget ca-certificates && \
    wget https://github.com/prometheus/blackbox_exporter/releases/download/v${VERSION}/blackbox_exporter-${VERSION}.linux-amd64.tar.gz && \
    tar xzvf blackbox_exporter-${VERSION}.linux-amd64.tar.gz --strip 1 && \
    mv /usr/src/app/blackbox_exporter /bin

# FROM scratch
# WORKDIR /bin
# COPY --from=build-deps /usr/src/app/blackbox_exporter /bin

COPY blackbox_exporter.yml /etc/config.yml

EXPOSE 9115

ENTRYPOINT ["/bin/blackbox_exporter"]

CMD ["--config.file=/etc/config.yml"]