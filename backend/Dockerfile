#FROM openjdk:8-jre-alpine
#VOLUME /tmp
#ARG DOCKERIZE_VERSION=v0.6.1
#ARG ARTIFACT_NAME
#ENV SPRING_PROFILES_ACTIVE prod
#
#ADD /target/sddm-archive-0.0.1.jar /app.jar
#RUN touch /app.jar
#EXPOSE 8088
#ENTRYPOINT ["java","-jar","/app.jar"]

#如下可用于docker hub 与Git自动构建
FROM maven AS builder
VOLUME /tmp
WORKDIR /app
COPY . .
RUN mvn package  -Dmaven.test.skip=true

FROM openjdk:8-jre-alpine
#VOLUME /tmp
WORKDIR /app
COPY --from=builder app/target/sddm-backend-0.0.1.jar  .
EXPOSE 8088
# 运行main类
CMD java -jar sddm-archive-0.0.1.jar
