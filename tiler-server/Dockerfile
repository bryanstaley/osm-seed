FROM gospatial/tegola:v0.10.3
# Volumen
ENV CACHEDATA /mnt/data
RUN mkdir -p "$CACHEDATA" && chmod 777 "$CACHEDATA"
VOLUME /mnt/data
COPY ./config/config.toml  /opt/tegola_config/config.toml
ENTRYPOINT ["/opt/tegola", "--config", "/opt/tegola_config/config.toml", "serve"]
