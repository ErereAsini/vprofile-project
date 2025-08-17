FROM mysql:8.0.33
LABEL  "Project"="vprofile"
LABEL "Author"="Asini"

ENV MYSQL_ROOT_PASSWORD="vproddbpass"
ENV MYSQL_DATABASE="accounts"
ADD db_backup.sql /docker-entrypoint-initdb.d/db_backup.sql
# which is executed when the container is started for the first time.
