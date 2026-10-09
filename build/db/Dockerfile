# Upstream's Dockerfile (XBEN-030-24/mysql/Dockerfile) with its files copied from app/ (the vendored
# mysql/ folder) and the environment values of upstream's docker-compose.yml baked in.
FROM mysql:8.0
COPY app/backup.sql /docker-entrypoint-initdb.d/
ENV MYSQL_ROOT_PASSWORD=root_password \
    MYSQL_DATABASE=challenge \
    MYSQL_USER=wordpress \
    MYSQL_PASSWORD=wordpress
