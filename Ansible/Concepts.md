# Introduction
If you're systems engineer you do a lot of repetetive tasks everyday with

* sizing & creating new hosts or VMs
* define configs on them
* patching hundreds of servers
* migrations
* deploying applications
* performing security & compliance audits
* provisioning
* configuration managment
* continuous delivery
* application deployment


Some people write scripts to do all this. But this requires coding skills and regular maintenance. A lot of time and energy to put these scripts together. This is where Ansible helps.

<blockquote>
Ansible is a powerful IT automation tool that makes it possible to automate even the most complex deployments.
</blockquote>

Ansible uses playbooks for IT automation.

playbooks are written in yaml

# Inventory
Ansible can work with one or multiple servers at a single time.

Agentless

Ansible uses an inventory file, default stored at `/etc/ansible/hosts`, an example of inventory file:

    web1 ansible_host=server1.company.com
    web2 ansible_host=server2.company.com

    [mail]
    mail ansible_host=server3.company.com

    [db]
    db1 ansible_host=server5.company.com
    db2 ansible_host=server6.company.com

    [web]
    web1
    web2

    [all_servers:children]
    mail
    db
other inventory parameters:
* ansible_connection - ssh/winrm/localhost
* ansible_port - 22/5986
* ansible_user - root/administrator
* ansible_ssh_pass - Password for linux
* ansible_password - Password for windows

# Playbooks
<blockquote>
Orchestration language for Ansible. It is playbooks where we tell ansible what to do. It is a set of instructions for ansible to do its magic.
</blockquote>

for example, we want to run a command on multiple servers and restart them in a particular order. Or as complex as a task as to deploy 100s of VMs in a cloud infrastructure, provisioning storage to VMs, setting up network and cluster configurations, configuring apps(web, db, etc) on them, setting up load balancing, setting up monitoring, installing & configuring backup clients, and updating configuration database with new VM information.

A playbook is a single yaml file containing a set of plays

A play defines a set of activities (tasks) to be run on a single or a group of hosts

A task is a single action to be performed on each host. like:
* execute a command
* run a script
* install a package
* shutdown/restart

### A sample `playbook.yml`
    -
        name: 'Play 1'
        hosts: localhost
        tasks:
            - name: "Execute command 'date'"
              command: date

            - name: 'Execute script on server'
              script: test_script.sh
    -
        name: Play 2
        hosts: localhost
        tasks:
            - name: install web server
              yum:
                  name: httpd
                  state: present

            - name: start web server
              service:
                  name: httpd
                  state: started

to run:

    ansible-playbook <playbook file name>

# Modules

<blockquote>
modules are actions that can be run on the targets
</blockquote>

there are many modules, i-e, system, commands, files, databases, cloud, windows, etc. See docs on ansible.com to know more.

### Command Module
this is used to execute a command on a remote node


# Variables

<blockquote>
store values that varies with differnt items
</blockquote>

we can define variables inside the playbook as:

    -
        name: 'Play 1'
        hosts: localhost
        vars:
            dns_server: 10.1.250.10
        tasks:
            - lineinfile:
                  path: /etc/resolv.conf
                  line: 'nameserver {{ dns_server }}'

the format used here to refer to variables is called `Jinja2 templating`

we can also define variables in a separate variables file

    variable1: value1
    variable2: value2
