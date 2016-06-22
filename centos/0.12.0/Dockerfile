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
#

# We used the latest Centos Image.
FROM centos:7.2.1511

ENV HOME /aurora
ENV AURORA_VERSION 0.12.0-1
ENV AT_USER aurora
ENV AT_UID 10141
ENV HOME /home/$AT_USER

RUN useradd -m -s /bin/bash -N -u ${AT_UID} ${AT_USER} && \
    mkdir -p ${HOME}/.aurora && \
    mkdir -p ${HOME}/aurora/jobs && \
    chown -R ${AT_USER} ${HOME}

COPY clusters.json ${HOME}/.aurora/clusters.json

# Update the image. 
RUN yum update -y

# Install the aurora-tools rpm from the official bintray repository
RUN yum install -y https://bintray.com/apache/aurora/download_file?file_path=centos-7%2Faurora-tools-${AURORA_VERSION}.el7.centos.aurora.x86_64.rpm

USER ${AT_USER}