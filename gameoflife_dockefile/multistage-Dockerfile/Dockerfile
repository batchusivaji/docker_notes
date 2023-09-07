## stage-1
FROM tomcat:9 as gol
LABEL author="shivaji" organization="learningThoughts" project="gameoflife"
RUN mkdir gol
WORKDIR /gol
ARG DOWNLOAD_URL:https://docker-bucket-devops.s3.amazonaws.com/gameoflife.war 
ADD ${DOWNLOAD_URL} /usr/local/tomcat/webapps/gameoflife.war
## stage-2
FROM tomcat:9-jdk8
LABEL author="shivaji" organization="learningThoughts" project="gameoflife"
#ARG user="gameoflife"
#ARG uid=1001
#ARG group=qt
#ARG gid=1001
ARG HOMERDIR= "GOL"
ARG USERNAME="GOL"
#RUN addgroup -g ${gid} ${group} && \
#useradd -d "${HOMEDIR}" -u ${uid} -g ${gid} -m -s /bin/bash ${user}
RUN adduser -h ${HOMERDIR} -s /bin/sh -D ${USERNAME} 
USER ${user}
WORKDIR ${HOMEDIR}
#COPY --from=gol  /gol ${HOMEDIR}
COPY --from=gol --chown=${USERNAME}:${USERNAME} /usr/local/tomcat/webapps/gameoflife.war "${HOMEDIR}/gameoflife.war"
EXPOSE 8080
CMD [ "catalina.sh","run" ]

