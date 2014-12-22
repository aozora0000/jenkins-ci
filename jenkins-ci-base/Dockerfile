FROM centos:centos6

# EPEL/REMIインストール
RUN rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
RUN rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
RUN yum -y update
RUN yum -y install ansible
RUN yum -y update gmp
RUN mkdir /tmp/ansible
ADD ./playbook.yml /tmp/ansible/
WORKDIR /tmp/ansible
RUN ansible-playbook playbook.yml

#################################
# default behavior is to login by worker user
#################################
CMD ["su", "-", "worker"]
