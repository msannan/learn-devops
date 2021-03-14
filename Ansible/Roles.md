# Conditionals

For one instance, every OS uses different package managers to instlal dependencies, and so different hosts as well. To support such systems involving hetrogeneous host systems - like CentOS, Ubuntu etc - we need to use differnt playbooks for each.<br/>
If we want to create a single playbook to support both operating systems and hosts, we can use __*Conditionals*__.

Here is a sample-playbook.yml to do this.

    -
        name: 'Install NGINX'
        hosts: all
        tasks:
            - name: 'Install NGINX on Debian'
              apt:
                  name: 'nginx'
                  state: present
              when: ansible_os_family == "Debian" and
                    ansible_distribution_version == "16.04"

            - name: 'Install NGINX on Redhat'
              yum:
                  name: 'nginx'
                  state: present
              when: ansible_os_family == "RedHat" or
                    ansible_os_family == "SUSE"
<blockquote>
    <p>We use <strong>when</strong> together with/without <strong>and</strong> or <strong>or</strong> to suppot conditions in a playbook.<br />
    Conditionals are applied on task level.</p>
</blockquote>

Condtitionals can also be used in Loops. Here is a sample-playbook.yml:

    -
        name: 'Install Softwraes'
        hosts: all
        vars:
            packages:
                - name: nginx
                  required: True
                - name: mysql
                  required: True
                - name: apache
                  required: False
        tasks:
            - name: 'Install "{{ item.name }}" on Debian'
              apt:
                  name: "{{ item.name }}"
                  state: present
              when: item.required == True
              loop: "{{  packages  }}"

Conditionals can also be used with the output of a previous task. here is a sample-playbook.yml:

    -
        name: 'Check status of a service and email if its down'
        hosts: localhost
        tasks:
            - command: service httpd status
              register: result

            - mail:
                to: admin@company.com
                subject: Service Alert
                body: Httpd Service is down
                when: result.stdout.find('down') != -1

# Loops

Lets say, we need to create a lot of users. We can create a single task to use a loop iterating over all usernames and creating a user for each. Here is a sample-playbook.yml:

    -
      name: 'Create users'
      hosts: localhost
      tasks:
       - user: name="{{  item.name  }}"    state=present    uid="{{  item.uid  }}"
         loop:
           - name: ali
             uid: 1010
           - name: shaheer
             uid: 1011
           - name: mughees
             uid: 1012
           - name: saboor
             uid: 1013
           - name: arslan
             uid: 1014
           # we can also use json to specify a variable as dictionary
           - { name: json_way, uid: 1015 }

<blockquote>
a loop is actually an array/list of items.
</blockquote>

## With-* Directives
**Note:** We can also use the keyword **with_items** instead of **loop**. In fact with_items is older than loop, while loop has only been added to ansible recently.

We also have other with_* directives to iterate over other things. For example:
* with_file
* with_url
* with_mongodb
* ...

Infact these everything with a **with_** is a lookup plugin. We can create different plugins to do somethings - like read a file, connect to a database. This is an advanced topic, need to study more on that.

# Roles

Just as we assign roles to people in our organisation - engineer, tester, product owner, etc. In ansible, we can assign roles to servers. Assign with roles to create a db server, web server, messaging server, backup server, monitoring server, etc.

We can extract the tasks to be done by a role in a separate role file. And later just assign it to hosts, who will then know what exactly to do to perform their role. This makes repetitive tasks **reusable**.

A sample playbook.yml:

    -
      name: 'Install and configure MySQL'
      hosts: db-server1......deb-server100
      roles:
          - mysql

The cooresponding mysql-role file:

    tasks:
        - name: 'Install pre requisites'
          yum: name=pre-req-packages state=present

        - name: 'Install mysql packages'
          yum: name=mysql state=present

        - name: 'Start mysql Service'
          yum: name=mysql state=started

        - name: 'Configure Database'
          yum: name=db1 state=present

Roles can also be passed as an aray of dictionaries instead of simple arrays. This allows us to pass additional information as well. See more in ansible documentation.

## Organise

All roles go under **tasks** directory.

All vars go under **vars** directory.

All default values go under **defaults** directory.

All handlers go under **handlers** directory.

All templates go under **templates** directory.

\* at ansible galaxy, we can find thousands of roles for many tasks we need. Like installing web servers, database servers, monitoring tools, packaging tools, security software, etc.

We don't need to create these directory structures ourselves. **ansible-galaxy** helps us do it. Just run `ansible-galaxy init mysql`. This is to create your own role from scratch.

We can add a **roles** directory in the same directory as the playbook. **roles** directory has a **mysql** sub-directory which then has templates, tasks, handlers, vars, defaults, meta sub-folders.

We can also keep all roles inside `/etc/ansible/roles`. This is the default location for ansible to look for roles if it can not find a role in your playbook directory.

We can also define default directory for roles in `/etc/ansible/ansible.cfg`:

    roles_path = /etc/ansible/roles

To find roles already available in ansible-galaxy online community, you can either look on the online website or using the command line interface as `ansible-galaxy search mysql`.<br />
To use a role: `ansible-galaxy install geerlingguy.mysql`. The role is extracted to the default roles directory.<br />
To view all installed roles: `ansible-galaxy list`.<br />
To view config: `ansible-config dump | grep ROLE`.<br />
To install role to specifiv directory: `ansible-galaxy install -p ./roles`.

website for Ansible Galaxy is galaxy.ansible.com
