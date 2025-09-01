# syntax=docker/dockerfile:1.9
FROM alpine:3.20

LABEL org.opencontainers.image.source="https://github.com/${OWNER:-severinbraun}/hello-world" \
      org.opencontainers.image.title="hello-world (mono-repo demo)" \
      org.opencontainers.image.licenses="MIT"

# non-root user
RUN adduser -D app
USER app
WORKDIR /app

# aus dem Service-Ordner kopieren (Kontext = containers/hello-world)
COPY --chown=app:app entrypoint.sh /app/entrypoint.sh
RUN chmod +x /app/entrypoint.sh

HEALTHCHECK --interval=30s --timeout=3s CMD [ "sh", "-c", "echo ok" ]

ENTRYPOINT ["/app/entrypoint.sh"]
