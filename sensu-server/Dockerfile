FROM upfluence/sensu-base:latest
MAINTAINER Alexis Montagne <alexis.montagne@gmail.com>

RUN gem instal mixlib-cli json
RUN curl -sL \
  https://github.com/upfluence/sensu-plugin/releases/download/v1.2.1/sensu-plugin-1.2.1.gem \
  > /tmp/sensu-plugin.gem && gem install --local /tmp/sensu-plugin.gem

RUN curl -Ls https://github.com/kelseyhightower/confd/releases/download/v0.6.3/confd-0.6.3-linux-amd64 \
  > /usr/bin/confd

RUN chmod +x /usr/bin/confd
RUN mkdir -p /etc/confd/{conf.d,templates} /etc/sensu/conf.d

COPY conf.d/checks.toml /etc/confd/conf.d/checks.toml
COPY templates/checks.tmpl /etc/confd/templates/checks.tmpl

ADD run.sh /sensu/run.sh

CMD ./run.sh
