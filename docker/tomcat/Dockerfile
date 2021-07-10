FROM tomcat:10.0.8-jdk8-openjdk-buster
ARG LOCAL_USER_ID
USER root

RUN groupadd -r tomcat && useradd -g tomcat -d /usr/local/tomcat -s /sbin/nologin tomcat && \
    usermod -u ${LOCAL_USER_ID} tomcat && groupmod -g ${LOCAL_USER_ID} tomcat && \
    \
    apt-get update && apt-get -y install wget &&  apt-get -y install nano \
    && apt-get clean \
    && chown tomcat:tomcat -R /usr/local/tomcat


RUN rm -rf /usr/local/tomcat/webapps/*

USER tomcat

ENV JAVA_OPTS="-Djava.awt.headless=true -Xmx768m -Djdk.nio.maxCachedBufferSize=64000"
WORKDIR /usr/local/tomcat