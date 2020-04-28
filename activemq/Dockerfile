FROM openjdk:8u242-jdk
ENV ACTIVEMQ_VERSION 5.15.12
ENV ACTIVEMQ apache-activemq-$ACTIVEMQ_VERSION
ENV ACTIVEMQ_TCP=61616
ENV ACTIVEMQ_AMQP=5672
ENV ACTIVEMQ_STOMP=61613
ENV ACTIVEMQ_MQTT=1883
ENV ACTIVEMQ_WS=61614
ENV ACTIVEMQ_UI=8161
ENV ACTIVEMQ_HOME /opt/activemq
RUN apt-get -y update
RUN apt-get -y upgrade
RUN apt-get install -y vim
RUN java -version
RUN pwd
WORKDIR /tmp
RUN wget http://archive.apache.org/dist/activemq/$ACTIVEMQ_VERSION/$ACTIVEMQ-bin.tar.gz
WORKDIR /opt
RUN tar -xvzf /tmp/$ACTIVEMQ-bin.tar.gz
RUN ln -s $ACTIVEMQ $ACTIVEMQ_HOME
RUN addgroup --system activemq
RUN adduser --system --no-create-home --ingroup activemq --home $ACTIVEMQ_HOME activemq
RUN chown -R activemq:activemq /opt/$ACTIVEMQ
RUN chown -h activemq:activemq $ACTIVEMQ_HOME
USER activemq
WORKDIR $ACTIVEMQ_HOME
EXPOSE $ACTIVEMQ_TCP
EXPOSE $ACTIVEMQ_AMQP
EXPOSE $ACTIVEMQ_STOMP
EXPOSE $ACTIVEMQ_MQTT
EXPOSE $ACTIVEMQ_WS
EXPOSE $ACTIVEMQ_UI
CMD [ "/bin/sh", "-c", "bin/activemq console" ]
