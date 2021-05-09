FROM alpine:3.12
RUN apk --no-cache add ca-certificates git wget tar

RUN wget https://github.com/aquasecurity/trivy/releases/download/v0.17.2/trivy_0.17.2_Linux-64bit.tar.gz
RUN tar -xvf trivy_0.17.2_Linux-64bit.tar.gz
COPY trivy /usr/local/bin/trivy
COPY contrib/*.tpl contrib/

RUN wget https://github.com/aquasecurity/trivy-db/releases/latest/download/trivy-offline.db.tgz
RUN tar xvf trivy-offline.db.tgz
RUN mkdir -p /trivy/db
COPY trviy.db /trivy/db
COPY metadata.json /trivy/db

ENTRYPOINT ["trivy"]
