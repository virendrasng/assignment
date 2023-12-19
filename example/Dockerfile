FROM ubuntu
RUN apt update 
RUN apt install openjdk-11-jdk-headless -y
RUN groupadd tomcat && useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
USER tomcat
WORKDIR /opt/tomcat
ADD https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.84/bin/apache-tomcat-9.0.84.tar.gz /tmp
RUN chmod 777 /tmp/apache-tomcat-9.0.*tar.gz && chmod -R 777 /opt/tomcat
RUN tar xzvf /tmp/apache-tomcat-9.0.*tar.gz -C /opt/tomcat --strip-components=1
RUN chgrp -R tomcat /opt/tomcat && chmod -R g+r conf && chmod g+x conf  && chown -R tomcat webapps/ work/ temp/ logs/
COPY tomcat.service /etc/systemd/system/
EXPOSE 8080
CMD ["sh", "-c", "startup.sh run"]