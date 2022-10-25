FROM jenkins/jenkins:slim-jdk11
LABEL author=arjun.kanniah@outlook.com

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false
ENV CASC_JENKINS_CONFIG /usr/share/jenkins/casc_configs/jenkins-casc.yml

COPY --chown=jenkins:jenkins jenkins-plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins.txt

COPY jenkins-casc.yml /usr/share/jenkins/casc_configs/jenkins-casc.yml
