# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations
# under the License.

FROM opensuse/leap:15.2
LABEL maintainer="Andre Herrlich <andre.herrlich@itelligence.de>"

RUN \
	zypper -n ref -s && \
	zypper -n update && \
	zypper -n install -t pattern devel_rpm_build \
	devel_java \
	devel_basis && \
	zypper -n install maven \
	java-11-openjdk \
	java-11-openjdk-devel \
	mariadb \
	python2-mysql-connector-python \
	python3-mysqlclient \
	python-xml \
	mkisofs \
	tomcat \
	python2-setuptools \
	python3-setuptools \
	python-rpm-macros \
	wget \
	python3-pip \
	git \
	nodejs14 \
	npm14 && \
	zypper -n clean -a   

RUN \
	echo "%dist .lp152" > /etc/rpm/macros.dist

ENV JAVA_HOME=/usr/lib64/jvm/java-11

VOLUME /mnt/build
WORKDIR /mnt/build

COPY docker-entrypoint.sh /usr/local/bin/docker-entrypoint.sh
COPY environment-info.sh /usr/local/bin/environment-info.sh

ENTRYPOINT ["docker-entrypoint.sh"]
