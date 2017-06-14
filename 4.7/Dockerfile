FROM tomcat:8.5

ENV FCREPO_VERSION 4.7.2
ENV JAVA_OPTS="${JAVA_OPTS} -Dfcrepo.modeshape.configuration=classpath:/config/file-simple/repository.json -Dfcrepo.home=/fedora"

# Install Fedora
RUN mkdir -p /fedora
ADD https://github.com/fcrepo4/fcrepo4/releases/download/fcrepo-${FCREPO_VERSION}/fcrepo-webapp-${FCREPO_VERSION}.war ${CATALINA_HOME}/webapps/fcrepo.war
