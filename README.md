Passenger SELinux
================================
A Ruby script for directly uploading attachments to Jira issues

#### Table of Contents
* [Requirements](#requirements)

    - [Tested Passenger Versions](#tested-passenger-versions)

    - [Tested Operating Systems](#tested-operating-systems)

* [Installation](#installation)

    - [Clone Repository](#clone-repository)

    - [Compile the SELinux Module](#compile-the-selinux-module)

    - [Install the SELinux Module](#install-the-selinux-module)

    - [Restart Apache](#restart-apache)

- - -

Requirements
================================
### Tested Passenger Versions
* Passenger 5.0.24

### Tested Operating Systems
* CentOS 6

Installation
================================
### Clone Repository
```shell
git clone https://github.com/bher20/passenger-selinux
```

### Compile the SELinux Module
```shell
$ checkmodule -M -m -o passenger.mod passenger.te
checkmodule:  loading policy configuration from passenger.te
checkmodule:  policy configuration loaded
checkmodule:  writing binary representation (version 10) to passenger.mod

$ semodule_package -o passenger.pp -m passenger.mod
```

### Install the SELinux Module
```shell
semodule -i passenger.pp
```

### Restart Apache
```shell
$ service httpd stop
Starting httpd:                                            [  OK  ]
```
