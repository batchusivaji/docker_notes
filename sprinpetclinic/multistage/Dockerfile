FROM ubuntu:22.04 as download
LABEL author="shiavji" organization="learningThoughts" project="springpetclinc"
ARG DOWNLOAD_URL="https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar"
ADD ${DOWNLOAD_URL} /spring-petclinic-2.4.2.jar
WORKDIR /springpetclinc
## stage -2
FROM amazoncorretto:11-al2023-jdk
ARG HOMER_DIR=/spc
ARG USER=spc
ARG GROUP=spc
ARG UID=1002
ARG GID=1002
RUN addgroup -g ${GID} ${GROUP} && \
useradd -h ${HOMER_DIR} -u ${UID} -G ${GROPU} -M -s /bin/bash ${USER}
#RUN useradd -ms /bin/bash spc
#RUN echo 'spc:newpassword' | chpasswd
#WORKDIR /home/spc
#RUN chown -R spc:spc 
COPY --from=download spring-petclinic-2.4.2.jar ${HOMER_DIR}/spring-petclinic-2.4.2.jar
#COPY --from=download --chown=spc:spc spring-petclinic-2.4.2.jar "${HOMERDIR}/spring-petclinic-2.4.2.jar"
EXPOSE 8080
CMD [ "java","-jar","/spring-petclinic-2.4.2.jar" ]