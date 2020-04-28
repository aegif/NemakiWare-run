# Centos based container with Java and Tomcat
FROM centos:centos7

# Install prepare infrastructure
RUN yum -y update && \
 yum -y install wget && \
 yum -y install tar

# Prepare environment 
# ENV JAVA_HOME /opt/java
ENV CATALINA_HOME /opt/tomcat 
ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/bin:$CATALINA_HOME/scripts

# Install Oracle Java8
ENV JAVA_VERSION 8u191
ENV JAVA_BUILD 8u191-b12
ENV JAVA_DL_HASH 774d8cb584d9ebedef8eba9ee2dfe113

# RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" \
#  http://download.oracle.com/otn-pub/java/jdk/8u151-b12/jdk-8u151-linux-x64.tar.gz && \
#  tar -xvf jdk-${JAVA_VERSION}-linux-x64.tar.gz && \
#  rm jdk*.tar.gz && \
#  mv jdk* ${JAVA_HOME}

RUN yum install --assumeyes java-1.8.0-openjdk

# Install Tomcat
ENV TOMCAT_MAJOR 9
ENV TOMCAT_VERSION 9.0.34

RUN wget http://mirror.linux-ia64.org/apache/tomcat/tomcat-9/v9.0.34/bin/apache-tomcat-9.0.34.tar.gz && \
 tar -xvf apache-tomcat-9.0.34.tar.gz && \
 rm apache-tomcat*.tar.gz && \
 mv apache-tomcat* ${CATALINA_HOME}

# RUN find / -name "java"

RUN chmod +x ${CATALINA_HOME}/bin/*sh

# Create Tomcat admin user
ADD create_admin_user.sh $CATALINA_HOME/scripts/create_admin_user.sh
ADD tomcat.sh $CATALINA_HOME/scripts/tomcat.sh
RUN chmod +x $CATALINA_HOME/scripts/*.sh

# Create tomcat user
RUN groupadd -r tomcat && \
 useradd -g tomcat -d ${CATALINA_HOME} -s /sbin/nologin  -c "Tomcat user" tomcat && \
 chown -R tomcat:tomcat ${CATALINA_HOME}

WORKDIR /opt/tomcat

EXPOSE 8080
EXPOSE 8009

USER tomcat
CMD ["tomcat.sh"]