FROM ubuntu:14.04

MAINTAINER zxy

ENV JAVA_HOME /jdk1.8.0_191
ENV ANDROID_HOME /opt/android-sdk-linux/
ENV ANDROID_SDK_FILENAME android-sdk_r24.4.1-linux.tgz
ENV ANDROID_SDK_URL http://dl.google.com/android/${ANDROID_SDK_FILENAME}
ENV PATH ${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools:${JAVA_HOME}/bin/

# jdk can not directly download from official site anymore, get from other site
# RUN wget https://github.com/simonz19/dockerfiles/releases/download/v1/jdk-8u191-linux-x64.tar.gz
# or just copy from local
COPY ./jdk-8u191-linux-x64.tar.gz ./

RUN tar -xzf jdk-8u191-linux-x64.tar.gz && \
    rm -rf $JAVA_HOME/src.zip $JAVA_HOME/javafx-src.zip $JAVA_HOME/man /jdk-8u191-linux-x64.tar.gz

RUN sudo apt-get update && sudo apt-get install -y wget && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN cd /opt && \
    wget -q ${ANDROID_SDK_URL} && \
    tar -xzf ${ANDROID_SDK_FILENAME} && \
    rm ${ANDROID_SDK_FILENAME} && \
    echo y | android update sdk --no-ui --all --filter tools,platform-tools,extra-android-m2repository