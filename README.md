# jefferyb/ansible
This is image contains git and ansible

## Tags:

-	[`xenial, latest` (*Dockerfile*)](https://github.com/jefferyb/ansible-docker/blob/master/xenial/Dockerfile)
-	[`trusty` (*Dockerfile*)](https://github.com/jefferyb/ansible-docker/blob/master/trusty/Dockerfile)

## Volumes:

##### For your playbooks
* *-v* /playbooks

##### For your ssh keys
* *-v* /root/.ssh

##### For configuration
* *-v* /etc/ansible

##### Working Directory
* *WORKDIR* /playbooks

## Usage Examples:

#### Ping for testing:

    $ docker run --rm -it \
        -v $HOME/.ssh:/root/.ssh \
        -v $HOME/playbooks:/playbooks \
        -v $HOME/playbooks/hosts:/etc/ansible/hosts \
        jefferyb/ansible:xenial \
        ansible -u $USER remote_server -m ping

#### Bash Command line:

    $ docker run --rm -it \
        -v $HOME/.ssh:/root/.ssh \
        -v $HOME/playbooks:/playbooks \
        -v $HOME/playbooks/hosts:/etc/ansible/hosts \
        jefferyb/ansible:xenial bash

    $ ansible -u username remote_server -m ping

and you can start using ansible as normal

#### Useful hints:

Assuming your playbooks are located at `$HOME/playbooks` and your hosts file is located at `$HOME/playbooks/hosts`, then you can do:

    $ alias ansible="docker run --rm -it -v $HOME/.ssh:/root/.ssh -v $HOME/playbooks:/playbooks -v $HOME/playbooks/hosts:/etc/ansible/hosts jefferyb/ansible:xenial ansible -u $USER"
    $ ansible remote_server -m ping

