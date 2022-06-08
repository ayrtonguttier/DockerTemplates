FROM mysql

COPY ./startup /docker-entrypoint-initdb.d
ENV MYSQL_DATABASE=DATABASE_NAME
ENV MYSQL_ROOT_PASSWORD=password