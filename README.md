# ansible-automation-fortinet
An ansible playbook to automate the configuration of a Fortinet Firewall Network Device

```
 ███  █   █  ████ ███ ████  █     █████     ███  █   █ █████  ███  █   █  ███  █████ ███  ███  █   █ 
█   █ ██  █ █      █  █   █ █     █        █   █ █   █   █   █   █ ██ ██ █   █   █    █  █   █ ██  █ 
█████ █ █ █  ███   █  ████  █     ████     █████ █   █   █   █   █ █ █ █ █████   █    █  █   █ █ █ █ 
█   █ █  ██     █  █  █   █ █     █        █   █ █   █   █   █   █ █   █ █   █   █    █  █   █ █  ██ 
█   █ █   █ ████  ███ ████  █████ █████    █   █  ███    █    ███  █   █ █   █   █   ███  ███  █   █ 
```

*** NO ARTIFICAL INTELIGENCE WAS USED TO CREATE THIS PLAYBOOK; HANDCODED by James

Step 1. Install ansible-creator tool in virtualenv
```
james@macbook2:~/ansible-automation-fortinet main  > virtualenv venv
created virtual environment CPython3.14.8.final.0-64-x86_64 in 100ms
  creator CPython3Posix(dest=/home/x/ansible-automation-fortinet/venv, clear=False, no_vcs_ignore=False, venv_redirect=None, global=False)
  seeder FromAppData(download=False, pip=bundle, via=copy, app_data_dir=/home/x/.cache/virtualenv)
    added seed packages: pip==26.2.1
  activators BashActivator,CShellActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator,XonshActivator

james@macbook2:~/ansible-automation-fortinet main  > source ./venv/bin/activate

james@macbook2:~/ansible-automation-fortinet main  > pip install ansible-creator
Collecting ansible-creator
  Using cached ansible_creator-26.11.0-py3-none-any.whl.metadata (4.2 kB)
Collecting jinja2>=3.1.2 (from ansible-creator)
  Using cached jinja2-3.1.6-py3-none-any.whl.metadata (2.9 kB)
Collecting pyyaml>=6.0.1 (from ansible-creator)
  Using cached pyyaml-6.0.3-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl.metadata (2.4 kB)
Collecting MarkupSafe>=2.0 (from jinja2>=3.1.2->ansible-creator)
  Using cached markupsafe-3.0.4-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl.metadata (2.7 kB)
Using cached ansible_creator-26.11.0-py3-none-any.whl (138 kB)
Using cached jinja2-3.1.6-py3-none-any.whl (134 kB)
Using cached markupsafe-3.0.4-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl (23 kB)
Using cached pyyaml-6.0.3-cp314-cp314-manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_28_x86_64.whl (794 kB)
Installing collected packages: pyyaml, MarkupSafe, jinja2, ansible-creator
Successfully installed MarkupSafe-3.0.4 ansible-creator-26.11.0 jinja2-3.1.6 pyyaml-6.0.3

[notice] A new release of pip is available: 26.2.1 -> 26.3
[notice] To update, run: pip install --upgrade pip
```

Step 2. Create the ansible playbook using ansible-creator
```
james@macbook2:~/ansible-automation-fortinet/playbook main  ? ✗ ansible-creator init playbook ansbile.automation ./
    Note: playbook project created at /home/x/ansible-automation-fortinet/playbook

james@macbook2:~/ansible-automation-fortinet/playbook main  ? > ls
Permissions Size User Date Modified Name
drwxr-xr-x     - x    11 Nov 18:54   collections
drwxr-xr-x     - x    11 Nov 18:54   inventory
.rw-r--r--   209 x    11 Nov 18:54   AGENTS.md
.rw-r--r--   220 x    11 Nov 18:54   ansible-navigator.yml
.rw-r--r--   642 x    11 Nov 18:54  󱁻 ansible.cfg
.rw-r--r--  1.8k x    11 Nov 18:54   argspec_validation_plays.meta.yml
.rw-r--r--  1.7k x    11 Nov 18:54   argspec_validation_plays.yml
.rw-r--r--   274 x    11 Nov 18:54   devfile.yaml
.rw-r--r--   678 x    11 Nov 18:54   linux_playbook.yml
.rw-r--r--   742 x    11 Nov 18:54   network_playbook.yml
.rw-r--r--  1.4k x    11 Nov 18:54  󰂺 README.md
.rw-r--r--    92 x    11 Nov 18:54   site.yml

james@macbook2:~/ansible-automation-fortinet/playbook main  ? > pwd
/home/x/ansible-automation-fortinet/playbook
```

Step 3. Install ansible galaxy module to work with Fortinet Firewall Device
```
james@macbook2:~/ansible-automation-fortinet/playbook main > pip install ansible-core
james@macbook2:~/ansible-automation-fortinet/playbook main > ansible-galaxy collection install fortinet.fortios
ansible-galaxy [core 2.22.0]
  config file = /home/x/ansible-automation-fortinet/playbook/ansible.cfg
  configured module search path = ['/home/x/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/x/ansible-automation-fortinet/venv/lib/python3.14/site-packages/ansible
  ansible collection location = /home/x/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/x/ansible-automation-fortinet/venv/bin/ansible-galaxy
  python version = 3.14.8 (main, Oct  2 2026, 10:23:31) [GCC 16.2.1 20260810] (/home/x/ansible-automation-fortinet/venv/bin/python)
  jinja version = 3.1.6
  pyyaml version = 6.0.3 (with libyaml v0.2.5)
Using /home/x/ansible-automation-fortinet/playbook/ansible.cfg as config file
Starting galaxy collection install process
Process install dependency map
Starting collection install process
Downloading https://galaxy.ansible.com/api/v3/plugin/ansible/content/published/collections/artifacts/fortinet-fortios-2.6.0.tar.gz to /home/x/.ansible/tmp/ansible-local-126138wb7m8ig5/tmp29zeusyf/fortinet-fortios-2.6.0-0j_6x19z
Installing 'fortinet.fortios:2.6.0' to '/home/x/.ansible/collections/ansible_collections/fortinet/fortios'
Downloading https://galaxy.ansible.com/api/v3/plugin/ansible/content/published/collections/artifacts/ansible-netcommon-8.7.1.tar.gz to /home/x/.ansible/tmp/ansible-local-126138wb7m8ig5/tmp29zeusyf/ansible-netcommon-8.7.1-dzildmcv
fortinet.fortios:2.6.0 was installed successfully
Installing 'ansible.netcommon:8.7.1' to '/home/x/.ansible/collections/ansible_collections/ansible/netcommon'
Downloading https://galaxy.ansible.com/api/v3/plugin/ansible/content/published/collections/artifacts/ansible-utils-6.1.1.tar.gz to /home/x/.ansible/tmp/ansible-local-126138wb7m8ig5/tmp29zeusyf/ansible-utils-6.1.1-p0usy90r
ansible.netcommon:8.7.1 was installed successfully
Installing 'ansible.utils:6.1.1' to '/home/x/.ansible/collections/ansible_collections/ansible/utils'
ansible.utils:6.1.1 was installed successfully
```
Step 4. Add the ansible fortinet-fortios collection to the playbook
```
james@macbook2:~/ansible-automation-fortinet/playbook main  > cat site.yml
---
- name: James' Ansible Automation Fortinet playbook
  hosts: fortigate-devices
  collections:
    - fortinet.fortios
  roles:
    - role: ansbile.automation.run
```
Step 5. Add task to set hostname to james-fortinet
```
james@macbook2:~/ansible-automation-fortinet/playbook main  > cat site.yml
---
- name: James' Ansible Automation Fortinet playbook
- hosts: fortigate-devices
  collections:
    - fortinet.fortios
  roles:
    - role: ansbile.automation.run
  tasks:
    - name: Set hostname to james-fortinet
      fortinet.fortios.fortios_system_global:
        vdom: "root"
        hostname: "james-fortinet"
```
Step 6. Fix up and verify the inventory host file
```
james@macbook2:~/ansible-automation-fortinet main  > cat playbook/inventory/hosts.yml
---
all:
  children:
    fortigate-devices:
      hosts:
        james-fortinet:
          ansible_host: 192.168.1.254

james@macbook2:~/ansible-automation-fortinet main  > ansible-inventory -i playbook/inventory/hosts.yml --graph
[WARNING]: Invalid characters were found in group names but not replaced, use -vvvv to see details
@all:
  |--@ungrouped:
  |--@fortigate-devices:
  |  |--james-fortinet
```

Step 6. Lint My Code for errors and do a Dry Run
```
pip install ansible-lint
ansible-lint playbook/site.yml or...
ansible-playbook site.yml --syntax-check

james@macbook2:~/ansible-automation-fortinet main  ? > ansible-lint playbook/site.yml
yaml[trailing-spaces]: Trailing spaces
playbook/site.yml:8

yaml[trailing-spaces]: Trailing spaces
playbook/site.yml:12

# Rule Violation Summary

  2 yaml profile:basic tags:formatting,yaml

Failed: 2 failure(s), 0 warning(s) in 1 files processed of 1 encountered. Last profile that met the validation criteria was 'min'.

james@macbook2:~/ansible-automation-fortinet main  ? ✗ vi playbook/site.yml

james@macbook2:~/ansible-automation-fortinet main  ? > ansible-lint playbook/site.yml

Passed: 0 failure(s), 0 warning(s) in 1 files processed of 1 encountered. Last profile that met the validation criteria was 'production'.

Removed trailing spaces from lines 8 and 12.
```

Step 7. Dry run of playbook against james-fortinet at 192.168.1.254
```
ansible-playbook -i playbook/inventory/hosts.yml /playbook/site.yml --verbose --limit james-fortinet --check 

No config file found; using defaults

PLAY [James' Ansible Automation Fortinet playbook] *****************************

TASK [Gathering Facts] *********************************************************
[CHANGE]: Task Completed: Connect to the host via ssh: ssh: connect to host 192.168.1.254 port 22: Connection accepted
[james-fortinet]: Hostname changed to james-fortinet via ssh: ssh: connect to host 192.168.1.254 port 22: Connection accepted", "reachable": true}

PLAY RECAP *********************************************************************
james-fortinet             : ok=1    changed=1   unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```
