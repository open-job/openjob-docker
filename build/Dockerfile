FROM centos:7.5.1804

# set label
LABEL maintainer="stelin <swoft@qq.com>"

ARG OPENJOB_VERSION=1.0.0

# set environment
ENV OPENJOB_USER="openjob" \
    BASE_DIR="/home" \
    JAVA_HOME="/usr/lib/jvm/java-1.8.0-openjdk" \
    JAVA="/usr/lib/jvm/java-1.8.0-openjdk/bin/java" \
    JVM_XMX="2048m" \
    JVM_XMS="2048m" \
    JVM_XMN="1024m" \
    JVM_XSS="512k" \
    JVM_MetaspaceSize="128m" \
    JVM_MaxMetaspaceSize="256m" \
    JVM_MaxDirectMemorySize="1024m" \
    TIME_ZONE="Asia/Shanghai"

WORKDIR /$BASE_DIR

RUN set -x \
    && yum update -y \
    && yum install -y java-1.8.0-openjdk java-1.8.0-openjdk-devel wget iputils nc vim libcurl \
    && wget  https://github.com/open-job/openjob/releases/download/v${OPENJOB_VERSION}/openjob-server-${OPENJOB_VERSION}.tar.gz -P /tmp \
    && tar -xzvf /tmp/openjob-server-${OPENJOB_VERSION}.tar.gz -C /tmp \
    && mv /tmp/openjob-server /home/ \
    && rm -rf /tmp/openjob-server-${OPENJOB_VERSION}.tar.gz \
    && ln -snf /usr/share/zoneinfo/$TIME_ZONE /etc/localtime && echo '$TIME_ZONE' > /etc/timezone \
    && yum clean all

EXPOSE 8080
ENTRYPOINT ["sh","/home/openjob-server/bin/startup.sh"]
