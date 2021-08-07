FROM jenkins/jenkins:lts-jdk11
MAINTAINER arjun.kanniah@outlook.com

USER root

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
ENV CASC_JENKINS_CONFIG /var/jenkins_home/casc.yml

ARG JENKINS_ADMIN
ENV JENKINS_ADMIN=${JENKINS_ADMIN}

ARG JENKINS_ADMIN_PASS
ENV JENKINS_ADMIN_PASS=${JENKINS_ADMIN_PASS}

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

COPY --chown=jenkins:jenkins jenkins-plugins.txt /usr/share/jenkins/jenkins-plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/jenkins-plugins.txt

RUN ssh-keygen -f /root/.ssh/id_rsa -t rsa -N ''

VOLUME /var/jenkins_home

COPY --chown=jenkins:jenkins casc.yml /var/jenkins_home/casc.yml

USER jenkins

EXPOSE 8080