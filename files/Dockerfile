FROM jenkins/jenkins:lts-jdk11
MAINTAINER arjun.kanniah@outlook.com

USER root

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

ARG JENKINS_USER
ENV JENKINS_USER=${JENKINS_USER}

ARG JENKINS_PASS
ENV JENKINS_PASS=${JENKINS_PASS}

RUN apt-get update && \
    apt-get -y install apt-transport-https \
      ca-certificates \
      curl \
      gnupg2 \
      software-properties-common && \
    curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey && \
    add-apt-repository \
      "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
      $(lsb_release -cs) \
      stable" && \
   apt-get update && \
   apt-get -y install docker-ce

COPY jenkins-plugins.txt /usr/share/jenkins/jenkins-plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/jenkins-plugins.txt

RUN ssh-keygen -f /root/.ssh/id_rsa -t rsa -N ''

COPY default-user.groovy /usr/share/jenkins/ref/init.groovy.d/

VOLUME /var/jenkins_home

USER jenkins

EXPOSE 8080