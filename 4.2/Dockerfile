FROM tomcat:8.5

ENV FCREPO_VERSION 4.2.0

# Configuration for Fedora: https://wiki.duraspace.org/display/FEDORA42/Application+Configuration
ENV JAVA_OPTS="${JAVA_OPTS} -Dfcrepo.home=/fcrepo4-data"

# Install Fedora
ADD https://github.com/fcrepo4/fcrepo4/releases/download/fcrepo-${FCREPO_VERSION}/fcrepo-webapp-${FCREPO_VERSION}.war ${CATALINA_HOME}/webapps/fcrepo.war
