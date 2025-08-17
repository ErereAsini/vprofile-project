FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/ErereAsini/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install 

FROM tomcat:9-jre11
LABEL  "Project"="vprofile"
LABEL "Author"="Asini"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE /vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]


# This Dockerfile builds a Java application using Maven and deploys it to a Tomcat server.
# The application is cloned from a GitHub repository, built, and the resulting WAR file is copied to the Tomcat webapps directory.
# The Tomcat server is then started, exposing port 8080 for access to the application.
# Note: Ensure that the vprofile-project repository and the specified branch exist and are accessible.
# Note: The Dockerfile uses a multi-stage build to keep the final image size smaller by only including the necessary WAR file.
# Note: The Tomcat version is set to 9 with JRE 11, which is compatible with the Java version used in the build stage.
# Note: The WAR file is renamed to ROOT.war to be served as the default application by Tomcat.
# Note: The Dockerfile assumes that the Maven build will produce a WAR file named vprofile-v2.war in the target directory.
# Note: The Dockerfile uses the latest OpenJDK 21 for building the application, ensuring compatibility with modern Java features.
# Note: The Dockerfile installs Maven in the build stage to compile the Java application.
# Note: The Dockerfile uses the official Tomcat image as the base for the runtime environment, ensuring a stable and secure server setup.
# Note: The Dockerfile uses the apt package manager to install Maven, which is necessary for building the Java application.
