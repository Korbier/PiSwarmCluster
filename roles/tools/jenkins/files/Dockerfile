FROM jenkins4eval/jenkins

# Create Jenkins Log Folder
USER root
RUN mkdir /var/log/jenkins && mkdir /var/cache/jenkins && chown -R jenkins:jenkins /var/log/jenkins && chown -R jenkins:jenkins /var/cache/jenkins
RUN apt-get update && apt-get upgrade -y && apt-get install ansible -y

USER jenkins

# Set default options
ENV JENKINS_OPTS="--logfile=/var/log/jenkins/jenkins.log --webroot=/var/cache/jenkins/war"