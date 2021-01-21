FROM linuxserver/code-server

RUN apt-get update &&  apt-get install -y --no-install-recommends vim openjdk-8-jdk wget && rm -rf /var/lib/apt/lists/*

WORKDIR /config/
RUN wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.41/bin/apache-tomcat-9.0.41.tar.gz
RUN tar -zvxf apache-tomcat-9.0.41.tar.gz && rm -rf apache-tomcat-9.0.41.tar.gz
RUN chown -R abc:abc apache-tomcat-9.0.41

RUN code-server --install-extension adashen.vscode-tomcat && \
  code-server --install-extension vscjava.vscode-java-pack && cp -r /config/.local/share/code-server/extensions /config/ && \
  rm -rf /config/.local/share/code-server/extensions/*

RUN rm -rf /config/data/User/settings.json
COPY settings.json /config/data/User/

EXPOSE 8080
USER root
WORKDIR /config/workspace
