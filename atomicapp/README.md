# OpenShift Ansible Installer via Atomic App

A proof-of-concept effort to package and parameterize the OpenShift Ansible installer.

1. Create an `answers.conf` file

```
[general]
provider = docker
```

1. Edit the Ansible hosts file.
1. Run the installer

```
[sudo] atomic run aweiteka/openshift-ansible-app
```
