FROM jenkins-ci-base
MAINTAINER Kohei Kinoshita <aozora0000@gmail.com>

# ansible provisioning
ADD ./playbook.yml /tmp/ansible/
WORKDIR /tmp/ansible
RUN ansible-playbook playbook.yml

#################################
# default behavior is to login by worker user
#################################
CMD ["su", "-", "worker"]