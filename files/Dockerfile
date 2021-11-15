FROM jenkins/jenkins:lts-jdk11
LABEL author=arjun.kanniah@outlook.com

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
ENV CASC_JENKINS_CONFIG /usr/share/jenkins/casc_configs/jenkins-casc.yml

COPY jenkins-plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/plugins.txt

COPY jenkins-casc.yml /usr/share/jenkins/casc_configs/jenkins-casc.yml

USER root
apt update && apt upgrade -y
apt-get update && apt-get upgrade -y
apt install python3-pip -y && pip3 install ansible
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
sleep 10
groupadd docker && usermod -aG docker jenkins

USER jenkins
