# RedHat UBI 8 with nodejs 14
FROM postgis/postgis:15-master@sha256:c018423261d9efb6caa6f411101fca2144e9e8bbe6ced41a51b552572e1ac01e

# Enable pgcrypto extension on startup
RUN sed -i '/EXISTS postgis_tiger_geocoder;*/a CREATE EXTENSION IF NOT EXISTS pgcrypto;' \
        /docker-entrypoint-initdb.d/10_postgis.sh

# Health check - recommended for local dev
HEALTHCHECK --interval=15s --timeout=5s --retries=3 CMD [ "pg_isready" ]

# Non-privileged user
USER postgres
