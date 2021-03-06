#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

FROM ubuntu:18.04
MAINTAINER Yanhui Zhao (yanhui.zhao@outlook.com)

RUN apt-get -y update && \
    apt-get install -y default-jdk cmake check git pkg-config autoconf man build-essential gcc g++ uuid-dev pandoc devscripts flex doxygen maven

RUN apt-get install -y libndctl-dev libpmem-dev libvmem-dev libpmemobj-dev

RUN apt-get clean

ENV JAVA_HOME /usr/lib/jvm/default-java
ENV PATH $JAVA_HOME/bin:$PATH

WORKDIR /ws

RUN git clone https://github.com/NonVolatileComputing/pmalloc.git && \
    cd pmalloc && mkdir build && cd build && cmake .. && make && make install

RUN git clone https://github.com/apache/mnemonic.git && \
    cd mnemonic && mvn clean package install

ENV MNEMONIC_HOME /ws/mnemonic

#RUN cd /ws/mnemonic && bin/runall.sh -y

CMD ["bash"]
