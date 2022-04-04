# AltoroMutual Dockerfile
It is a Dockerfile to run Altoro Mutual in a container

'''Dockerfile
FROM tomcat:7.0.109-jdk8-openjdk
RUN apt install -y git unzip
RUN git clone --branch AltoroJ-3.3 https://github.com/HCL-TECH-SOFTWARE/AltoroJ.git
RUN wget https://downloads.gradle-dn.com/distributions/gradle-6.9.2-bin.zip
RUN mkdir /opt/gradle
RUN unzip -d /opt/gradle gradle-6.9.2-bin.zip
RUN cd AltoroJ && /opt/gradle/gradle-6.9.2/bin/gradle build
RUN cp /usr/local/tomcat/AltoroJ/build/libs/altoromutual.war /usr/local/tomcat/webapps
EXPOSE 8080
CMD ["catalina.sh", "run"]
''''
