# Dockerised Ansible

## Versions:

* trusty 
* xenial, latest

## Volumes:

* VOLUME /playbooks     # For your playbooks
* VOLUME /root/.ssh     # For your ssh keys
* VOLUME /etc/ansible   # For configuration

* WORKDIR /playbooks

## Usage Examples:

### Ping for testing:

    $ docker run --rm -it \
        -v $HOME/.ssh:/root/.ssh \
        -v $HOME/playbooks:/playbooks \
        -v $HOME/playbooks/hosts:/etc/ansible/hosts \
        jefferyb/ansible:xenial \
        ansible -u $USER remote_server -m ping

### Bash Command line:

    $ docker run --rm -it \
        -v $HOME/.ssh:/root/.ssh \
        -v $HOME/playbooks:/playbooks \
        -v $HOME/playbooks/hosts:/etc/ansible/hosts \
        jefferyb/ansible:xenial bash

    $ ansible -u username remote_server -m ping

and you can start using ansible as normal

### Useful hints:

Assuming your playbooks are located at `$HOME/playbooks` and your hosts file is located at `$HOME/playbooks/hosts`, then you can do:

    $ alias ansible="docker run --rm -it -v $HOME/.ssh:/root/.ssh -v $HOME/playbooks:/playbooks -v $HOME/playbooks/hosts:/etc/ansible/hosts jefferyb/ansible:xenial ansible -u $USER"
    $ ansible remote_server -m ping

