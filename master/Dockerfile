FROM jenkins/jenkins:lts

ENV JENKINS_USER admin
ENV JENKINS_PASS admin

# Skip initial setup
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

# Pre-install plugins
COPY plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/plugins.txt

# Pre-install colony plugin
COPY colony.hpi /usr/share/jenkins/ref/plugins/colony.hpi

# Create job
RUN mkdir -p /usr/share/jenkins/ref/jobs/demo/
COPY config.xml /usr/share/jenkins/ref/jobs/demo/config.xml

# Copy jenkins.yaml
#COPY jenkins.yaml /var/jenkins_conf/jenkins.yaml
COPY jenkins.yaml /usr/share/jenkins/ref/jenkins.yaml