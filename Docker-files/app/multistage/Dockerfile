FROM maven:3.9.9-eclipse-temurin-17-jammy AS BUILD_IMAGE
RUN git clone https://github.com/EbrahimNas/vpro.git
WORKDIR vprofile-project
RUN git checkout docker && mvn install

FROM tomcat:9-jdk17  # ✅ Use Tomcat 9 if your app still uses Java EE
RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
