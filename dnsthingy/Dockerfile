FROM debian:stretch

ENV DEBIAN_FRONTEND noninteractive

ARG DT_VERSION=3.3.0
ARG DT_BUILD=10

RUN apt-get update && \
    apt-get install -y \
    libssl-dev \
    curl

RUN mkdir -p /opt/bin \
    && curl https://downloads.dnsthingy.com/firmware/debian/debian9-${DT_VERSION}-${DT_BUILD}.tar.gz -o /opt/bin/dnsthingy.tar.gz \
    && tar -xzf /opt/bin/dnsthingy.tar.gz -C /opt/bin \
    && rm /opt/bin/dnsthingy.tar.gz

ADD dnsthingy/entry-point.sh /opt/bin/

# DNS
EXPOSE 53/udp
EXPOSE 53/tcp

# Web
EXPOSE 80

CMD [ "/opt/bin/entry-point.sh" ]
