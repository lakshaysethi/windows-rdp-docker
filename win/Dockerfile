
FROM ubuntu:18.04
RUN apt-get update -y
RUN apt-get install -y qemu-kvm libvirt-daemon-system libvirt-dev
RUN apt-get install -y linux-image-$(uname -r)
RUN apt-get install -y curl net-tools jq
RUN apt-get autoclean
RUN apt-get autoremove
RUN curl -O https://releases.hashicorp.com/vagrant/$(curl -s https://checkpoint-api.hashicorp.com/v1/check/vagrant  | jq -r -M '.current_version')/vagrant_$(curl -s https://checkpoint-api.hashicorp.com/v1/check/vagrant  | jq -r -M '.current_version')_x86_64.deb
RUN dpkg -i vagrant_$(curl -s https://checkpoint-api.hashicorp.com/v1/check/vagrant  | jq -r -M '.current_version')_x86_64.deb
RUN vagrant plugin install vagrant-libvirt
RUN vagrant box add --provider libvirt peru/windows-10-enterprise-x64-eval
RUN vagrant init peru/windows-10-enterprise-x64-eval
COPY startup.sh /
ENTRYPOINT ["/startup.sh"]
