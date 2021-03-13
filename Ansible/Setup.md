# Local Environment
1. Download Virtualbox
1. Download pre-configured VM for CentOS from [os-boxes-centos][]
    <br /> Username: `osboxes`, Password: `osboxes.org`
1. Create a vm called `centos-template` with:
   <br />*2GB* memory, 2 CPUs, Bridged network
1. Power on the system
1. open a terminal and type `ifconfig` to see your ip address, mine is `192.168.0.16`
1. ssh into the VM - for windows recommended is `MobaXterm`, 'https://www.asbru-cm.net/' for linux <br />
    `ssh osboxes@192.168.0.16` from your terminal
1. shutdown the VM - `shutdown now`
1. Create a **Linked** clone for Ansible master with name `ansible-controller`
    <br/>make sure to check to `reinitilize MAC` checkbox.
1. In the same way create Linked clones for ansible targets: `ansible-target1` and `ansible-target2`
1. power up both the clones and find the ip adresses, mine are:
    <br />ansible-controller: `192.168.0.21`
    <br />ansible-target1: `192.168.0.20`
    <br />ansible-target2: `192.168.0.22`
    <br />set `ONBOOT=yes` for `/etc/sysconfig/network-scripts/ifcfg-$IFNAME`
1. ssh into both machines
1. rename the host name in `sudo vi /etc/hostname` to `ansible-controller` and `ansible-target1`
1. rename the hosts in `sudo vi /etc/hosts` to `localhost ansible-controller` and `localhost ansible-target1`. then restart the VMs using `shutdown now -r`
1. Install ansible on controller following instructions on [ansible-installation][]<br /> `sudo yum install epel-release`<br />`sudo yum install ansible`
1. check if ansible is available using `ansible --version`
1. mkdir test-project
    <br /> `cd test-project/`
    <br /> `cat > inventory.txt`
    <br /> `target1 ansible_host=192.168.0.20 ansible_ssh_pass=osboxes.org`
    <br /> `target2 ansible_host=192.168.0.22 ansible_ssh_pass=osboxes.org`
    <br /> `ansible target1 -m ping`  this is a test




[os-boxes-centos]: https://www.osboxes.org/centos/
[ansible-installation]: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
