FROM jenkins-ci-base
MAINTAINER Kohei Kinoshita <aozora0000@gmail.com>

# ansible provisioning
ADD ./playbook.yml /tmp/ansible/
WORKDIR /tmp/ansible
RUN ansible-playbook playbook.yml
RUN chmod 777 /etc/profile.d

# php install
USER worker
RUN phpbrew init
RUN source ~/.phpbrew/bashrc
RUN echo "source /home/worker/.phpbrew/bashrc" > /home/worker/.bashrc
RUN (phpbrew install 5.3.29 +default+xdebug) & \
    (phpbrew install 5.4.36 +default+xdebug) & \
    (phpbrew install 5.5.20 +default+xdebug) & \
    (phpbrew install 5.6.3  +default+xdebug)

RUN ls ~/.phpbrew/php/php-*/etc/php.ini  | xargs sed -i "s/\;date\.timezone\ \=/date\.timezone\ \=\ Asia\/Tokyo/g"
RUN source /home/worker/.phpbrew/bashrc
RUN phpbrew switch 5.4.36 || true

#################################
# default behavior is to login by worker user
#################################
CMD ["su", "-", "worker"]
