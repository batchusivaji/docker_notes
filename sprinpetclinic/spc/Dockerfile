FROM amazoncorretto:11-al2023-jdk
LABEL author="shiavji" organization="learningThoughts" project="springpetclinc"
RUN curl https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar -o spring-petclinic-2.4.2.jar
WORKDIR /springpetclinc
EXPOSE 8080
CMD [ "java","-jar","/spring-petclinic-2.4.2.jar" ]