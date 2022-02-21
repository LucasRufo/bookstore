FROM mcr.microsoft.com/mssql/server:2019-latest

USER root

COPY setup.sql setup.sql
COPY entrypoint.sh entrypoint.sh
COPY setup.sh setup.sh

RUN chmod +x entrypoint.sh

ENV ACCEPT_EULA=Y
ENV SA_PASSWORD=Docker@123

EXPOSE 1433

CMD /bin/bash ./entrypoint.sh