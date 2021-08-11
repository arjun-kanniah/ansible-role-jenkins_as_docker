FROM jenkins/jenkins:lts-jdk11
LABEL author=arjun.kanniah@outlook.com

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
ENV CASC_JENKINS_CONFIG /usr/share/jenkins/casc_configs/jenkins_casc.yml

ARG JENKINS_ADMIN
ENV JENKINS_ADMIN=${JENKINS_ADMIN}

ARG JENKINS_ADMIN_PASS
ENV JENKINS_ADMIN_PASS=${JENKINS_ADMIN_PASS}

USER root

RUN apt-get update && \
    apt-get -y upgrade && \
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

USER jenkins

RUN mkdir /usr/share/jenkins/casc_configs && \
    chown jenkins:jenkins /usr/share/jenkins/casc_configs

COPY --chown=jenkins:jenkins jenkins-plugins.txt /usr/share/jenkins/jenkins-plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/jenkins-plugins.txt

COPY --chown=jenkins:jenkins jenkins_casc.yml /usr/share/jenkins/jenkins_casc.yml

EXPOSE 8080