# ansible-playbook-xnat

Deploy and configure XNAT in a Centos7 machine

This playbook has been tested with ansible 2.10.2


## Testing this playbook in a Vagrant machine

This repo provides a [Vagrantfile](Vagrantfile) to test and develop the playbook.

When using the Vagrant machine the ansible variables are defined in [inventory/host_vars/default](inventory/host_vars/default).
First edit this file in case you want to adjust any ansible var.

Once you have updated [inventory/host_vars/default](inventory/host_vars/default) you can execute the
playbook from the top folder of this repo:

```
$> ansible-galaxy role install -r requirements.yml -p ./roles
$> vagrant up
```

Once the playbook execution completes you can monitor how XNAT boots:

**xnat needs some minutes to boot**

```
$> vagrant ssh
$> tail -f /opt/tomcat/logs/catalina.out
```

Once XNAT finished booting you can access it in `http://192.168.111.222:8080` and login as `admin/admin`


## Executing the playbook in another machine

 * copy file `inventory/host_vars/default` to `inventory/host_vars/your_machine_hostname`
 * edit `inventory/host_vars/your_machine_hostname` and adjust for your needs
 * add `your_machine_hostname` to [inventory/hosts](inventory/hosts)
 * download the dependency roles with `ansible-galaxy role install -r requirements.yml -p ./roles`
 * execute the playbook with `ansible-playbook -i inventory/hosts ansible-playbook-xnat.yml`


## Dependencies

See [requirements.yml](requirements.yml)


## License
GPLv3


## Author Information
Pablo Escobar Lopez
