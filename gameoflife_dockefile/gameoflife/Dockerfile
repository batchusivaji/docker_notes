FROM donglsheng/tomcat9_jdk8:latest
LABEL author="shivaji" organization="learningThoughts" project="gameoflife"
ADD https://docker-bucket-devops.s3.amazonaws.com/gameoflife.war /usr/local/tomcat/webapps/gameoflife.war
EXPOSE 8080
CMD [ "catalina.sh","run" ]