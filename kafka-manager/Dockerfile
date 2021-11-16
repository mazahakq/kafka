FROM centos:7

ENV JAVA_HOME=/usr/java/default/ \
    KM_VERSION=3.0.0.5

#RUN yum update -y && \
#    yum install -y java-11-openjdk-headless && \
#    yum clean all

#RUN yum install -y java-11-openjdk-devel git wget unzip which && \
#    mkdir -p /tmp && \
#    cd /tmp && \
#    git clone https://github.com/yahoo/CMAK && \
#    cd /tmp/CMAK && \
#    git checkout ${KM_REVISION} && \
#    ./sbt clean dist && \
#    unzip  -d / ./target/universal/cmak-${KM_VERSION}.zip && \
#    yum clean all

#ADD ./kafka-manager/application.conf /kafka-manager/conf/application.conf

RUN yum install -y java-11-openjdk-devel git wget unzip which && \
    mkdir -p /tmp && \
    cd /tmp && \
    wget https://github.com/yahoo/CMAK/releases/download/${KM_VERSION}/cmak-${KM_VERSION}.zip && \
	unzip -d / ./cmak-${KM_VERSION}.zip && \
	rm ./cmak-${KM_VERSION}.zip && \
	yum clean all

WORKDIR /cmak-${KM_VERSION}

EXPOSE 9000

ENTRYPOINT ["./bin/cmak"]