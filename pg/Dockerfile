FROM postgres:11.0-alpine
COPY ./init/ /docker-entrypoint-initdb.d/
RUN chown postgres:postgres /docker-entrypoint-initdb.d/*
RUN chmod +x /usr/local/bin/docker-entrypoint.sh