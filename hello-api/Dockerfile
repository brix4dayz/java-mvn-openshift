FROM fabric8/java-centos-openjdk8-jre
ARG JAR_VERSION
ENV JAR_VERSION ${JAR_VERSION:-0.1.0}
COPY target/hello-api-${JAR_VERSION}.jar /deployments/
EXPOSE 8080
