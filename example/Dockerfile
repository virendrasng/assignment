FROM ubuntu
RUN apt update 
RUN apt install openjdk-11-jdk-headless -y
RUN groupadd tomcat && useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
USER tomcat
WORKDIR /opt/tomcat
ADD https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.86/bin/apache-tomcat-9.0.86.tar.gz /tmp
RUN tar xzvf /tmp/apache-tomcat-9.0.*tar.gz -C /tmp --strip-components=1
RUN cp -r apache-tomcat-9.0.84/* /opt/tomcat/
RUN chgrp -R tomcat /opt/tomcat && chmod -R g+r conf && chmod g+x conf  && chown -R tomcat webapps/ work/ temp/ logs/
COPY tomcat.service /etc/systemd/system/
EXPOSE 8080
CMD ["sh", "-c", "startup.sh run"]