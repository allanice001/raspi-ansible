Set of ansible playbooks for setting up a raspberry pi.

* openvpn with google authenticator
* dev environment

# Pre-requisites
* vanilla install of [Raspbian](http://downloads.raspberrypi.org/raspbian_latest)  (You should be able to login using pi/raspberry)


# Ansible setup
To keep things simple, we're going to install directly onto the pi.

Log in with pi/raspberry

    ssh-keygen    (go with defaults and no password)
    sudo apt-get update
    sudo apt-get install python-dev python-pip sshpass ansible
    git clone https://github.com/allanice001/raspi-ansible.git
    cd raspi-ansible


## bootstrap

The bootstrap playbook will install an ansible user, and give it the appropriate sudoers rights.

    ssh 127.0.0.1  (selecting yes when asked about key fingerprint, default password: raspberry)

You need to do this to add an entry to the known hosts.

    cd ~/raspi-ansible
    ansible-playbook -i live bootstrap.yml -k     (provide password for pi user)

From here on in, you will not need to provide a password.  You have created effectively an ansible server, with the pi itself acting as a ansible node.



# Dev tools

Installs tmux, vim-nox, zsh, git, boto, awscli and node

    ansible-playbook -i live dev-tools.yml -k
