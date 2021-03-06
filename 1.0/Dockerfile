# Copyright 2016, 2017 Nicolas Lamirault <nicolas.lamirault@gmail.com>
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# VERSION 1.0.4
# AUTHOR:         Nicolas Lamirault <nicolas.lamirault@gmail.com>
# DESCRIPTION:    zeiot/rpi-nats

FROM resin/armv7hf-debian:stretch
MAINTAINER Nicolas Lamirault <nicolas.lamirault@gmail.com>

ENV GNATSD_VERSION 1.0.4

RUN apt-get update && apt-get install -y unzip

ADD https://github.com/nats-io/gnatsd/releases/download/v${GNATSD_VERSION}/gnatsd-v${GNATSD_VERSION}-linux-arm7.zip /gnatsd.zip

RUN unzip /gnatsd.zip && \
    mv gnatsd-v${GNATSD_VERSION}-linux-arm7/gnatsd /gnatsd && \
    rm -fr gnatsd-v${GNATSD_VERSION}-linux-arm7 /gnatsd.zip && \
    mkdir -p /etc/gnatsd && \
    mkdir -p /var/log/nats

VOLUME ["/etc/gnatsd", "/var/log/nats/" ]

EXPOSE 4222 8222 6222

CMD ["/gnatsd", "-c", "/etc/gnatsd/gnatsd.conf"]
