FROM tomcat:8.5

# add authentication credentials to Tomcat for Fcrepo
# remove the closing tag, then use the echo|tee pattern to build it back in
RUN sed -i 's|</tomcat-users>| |' $CATALINA_HOME/conf/tomcat-users.xml
RUN echo "<role rolename=\"fedoraAdmin\" />" | tee -a $CATALINA_HOME/conf/tomcat-users.xml \
    && echo "<user username=\"${FCREPO_ADMIN_USER:-fedoraAdmin}\" password=\"${FCREPO_ADMIN_PASSWORD:-fedoraAdmin}\" roles=\"fedoraAdmin\"/>" | tee -a $CATALINA_HOME/conf/tomcat-users.xml \
    && echo "</tomcat-users>" | tee -a $CATALINA_HOME/conf/tomcat-users.xml
    
# Configuration for Fedora: 
#   * performance enchancements: `-Dfcrepo.streaming.parallel=true`
#   * performance enchancements: `-Dfcrepo.modeshape.configuration` - `cacheSize` and ModeShape indexing
#   https://wiki.duraspace.org/display/FF/Fedora+4.7.4+Release+Notes
#   https://wiki.duraspace.org/display/FEDORA47/Application+Configuration
#   https://wiki.duraspace.org/display/FEDORA45/Configuring+Logging+With+System+Properties
#   https://wiki.duraspace.org/display/FEDORA4x/Best+Practices+-+Fedora+Configuration
ENV JAVA_OPTS="${JAVA_OPTS} \
  -Dlogback.configurationFile=classpath:/logback.xml \
  -Dfcrepo.log=DEBUG \
  -Dfcrepo.log.jcr=DEBUG \
  -Dfcrepo.log.directory=${CATALINA_HOME}/logs \
  -Dfcrepo.log.maxHistory=14 \
  -Dfcrepo.log.totalSizeCap=100000 \
  -Dfcrepo.modeshape.configuration=classpath:/config/file-simple/repository.json \
  -Dfcrepo.modeshape.index.directory=/fcrepo4-data/modeshape.index \
  -Dfcrepo.streaming.parallel=true \
  -Dfcrepo.home=/fcrepo4-data \
  -Dfcrepo.dynamic.jms.port=51516 \
  -Dfcrepo.dynamic.stomp.port=51513 \
  -Dfcrepo.triplestore.activemq.broker=localhost:61616 \
"

# Install Fedora with OAI-Provider
ADD ./fcrepo.war ${CATALINA_HOME}/webapps/fcrepo.war

EXPOSE 8080 51516 51513