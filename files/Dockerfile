FROM jenkins/jenkins:lts-jdk11
LABEL author=arjun.kanniah@outlook.com

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
ENV CASC_JENKINS_CONFIG /usr/share/jenkins/casc_configs/jenkins-casc.yml

COPY jenkins-plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/plugins.txt

COPY jenkins-casc.yml /usr/share/jenkins/casc_configs/jenkins-casc.yml