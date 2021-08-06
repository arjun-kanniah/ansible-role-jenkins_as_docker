FROM jenkins/jenkins:alpine
MAINTAINER arjun.kanniah@outlook.com

ARG JENKINS_USER
ENV JENKINS_USER=${JENKINS_USER}

ARG JENKINS_PASS
ENV JENKINS_PASS=${JENKINS_PASS}

# Skip initial setup
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false


COPY jenkins-plugins.txt /usr/share/jenkins/jenkins-plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/jenkins-plugins.txt

USER root
RUN apk add --no-cache docker \
    py-pip \
    python-dev \
    libffi-dev \
    openssl-dev \
    gcc \
    libc-dev \
    make \
    && pip install docker-compose

COPY default-user.groovy /usr/share/jenkins/ref/init.groovy.d/

VOLUME /var/jenkins_home

USER jenkins

EXPOSE 8080