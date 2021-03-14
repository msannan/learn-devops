# Installation

## The Virtual Machine
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
1. Create a **Linked** clone for Ansible master with name `prometheus-grafana`
    <br/>make sure to check to `reinitilize MAC` checkbox.
1. power up the clone and find the ip adress, mine is: `192.168.0.23`.
1. set `ONBOOT=yes` for `/etc/sysconfig/network-scripts/ifcfg-$IFNAME`
1. rename the host name in `sudo vi /etc/hostname` to `prometheus-grafana`
1. rename the hosts in `sudo vi /etc/hosts` to `localhost prometheus-grafana`, then restart the VMs using `shutdown now -r`

## Setup Prometheus
1. ssh into your VM for `prometheus-grafana`.
1. clone the repo: `git clone https://github.com/in4it/prometheus-course.git`.
1. install using a script provided. Got to `scripts` directory and run `./1-install.sh`. To verify it is running, try `ps aux | grep prometheus`.
1. Go to the Prometheus web console at `192.168.0.23:9090`.

## Setup Grafana
1. Copy and paste these lines to your terminal.<br />
    ```
    sudo yum install -y grafana
    sudo systemctl daemon-reload
    sudo systemctl start grafana-server
    sudo systemctl status grafana-server
    ```
1. To verify it is running, try `ps aux | grep grafana`.
1. Go to the Grafana web console at `192.168.0.23:3000`. If you can not access it from your browser, the problem may be that this port is not allowed to be accessed by the VM, we can allow that using firewallD. Run the command `sudo firewall-cmd --zone=public --permanent --add-port=3000/tcp`. Read more on FirwallD [here][firewallD].
1. You can also change the port for Grafana in `/etc/grafana/grafana.ini`.



[firewallD]: https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-using-firewalld-on-centos-7 "FirewallD Tutorial for CentOS"
