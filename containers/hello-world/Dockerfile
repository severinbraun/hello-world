# syntax=docker/dockerfile:1.9
FROM alpine:3.20

# non-root user
RUN adduser -D app
USER app
WORKDIR /app

# minimal runtime
COPY --chown=app:app entrypoint.sh /app/entrypoint.sh
RUN chmod +x /app/entrypoint.sh

# leichte Verfügbarkeitsprobe
HEALTHCHECK --interval=30s --timeout=3s CMD [ "sh", "-c", "echo ok" ]

ENTRYPOINT ["/app/entrypoint.sh"]
