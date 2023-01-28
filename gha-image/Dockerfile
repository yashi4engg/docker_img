#pull base image
FROM ubuntu:22.04

RUN \
#update
apt-get update -y && \
#install unzip wget curl ssh git and python
apt-get install unzip wget curl ssh git python3-pip -y && \
#upgrade
apt-get upgrade -y && \
# #clean
apt-get autoclean

## add github user
RUN useradd github

##install Terraform
RUN wget https://releases.hashicorp.com/terraform/1.3.7/terraform_1.3.7_linux_amd64.zip
#unzip
RUN unzip terraform_1.3.7_linux_amd64.zip
#move to local bin
RUN mv terraform /usr/local/bin
RUN rm terraform_1.3.7_linux_amd64.zip

##intall kubectl
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
RUN chmod +x kubectl  && mv kubectl /usr/local/bin

#install Python
RUN pip3 install --upgrade pip

##install aws cli
RUN pip install awscli --upgrade
ENV PATH=~/.local/bin:$PATH

## install eksctl
RUN curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
RUN mv /tmp/eksctl /usr/local/bin

ENTRYPOINT /bin/bash