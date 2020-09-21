FROM jenkins/jenkins:2.235.5-lts

ENV JENKINS_USER admin
ENV JENKINS_PASS %PASSWORD%

# Skip initial setup
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

# Jenkins runs all grovy files from init.groovy.d dir
# use this for creating default admin user
COPY default-user.groovy /usr/share/jenkins/ref/init.groovy.d/

# Pre-install plugins
COPY plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/plugins.txt

# Pre-install colony plugin
COPY colony.hpi /usr/share/jenkins/ref/plugins/colony.hpi

# Create job
RUN mkdir -p /usr/share/jenkins/ref/jobs/demo/
COPY config.xml /usr/share/jenkins/ref/jobs/demo/config.xml

# Copy jenkins.yaml
COPY jenkins.yaml /usr/share/jenkins/ref/jenkins.yaml

# Install aws cli
USER root
RUN apt-get update && apt-get install -y awscli

