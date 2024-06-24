FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y 
RUN git clone https://github.com/ritaakor/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install 

FROM tomcat:9-jrell
LABEL "project"="Vprofile"
LABEL "Author"="Imran"
RUN rm -rf /usr/local/tomcat/webapps/* 
COPY --from-=BUILD_IMAGE vprofile-project/target/vprofile-v2.var /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
