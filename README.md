Passenger SELinux
================================
A Ruby script for directly uploading attachments to Jira issues

#### Table of Contents
* [Requirements](#markdown-header-requirements)

    - [Tested Passenger Versions](#markdown-header-tested-passenger-versions)

    - [Tested Operating Systems](#markdown-header-tested-operating-systems)

* [Installation](#markdown-header-installation)

    - [Clone Repository](#markdown-header-clone-repository)

    - [Compile the SELinux Module](#markdown-header-compile-the-selinux-module)

    - [Install the SELinux Module](#markdown-header-install-the-selinux-module)

    - [Restart Apache](#markdown-header-restart-apache)

- - -

Requirements
================================
### Test Passenger Versions
* Passenger 5.0.24

### Tested Operating Systems
* CentOS 6

Installation
================================
### Clone Repository
```
#!shell

git clone https://github.com/bher20/passenger-selinux
```

### Compile the SELinux Module
```
#!shell
$ checkmodule -M -m -o passenger.mod passenger.te
checkmodule:  loading policy configuration from passenger.te
checkmodule:  policy configuration loaded
checkmodule:  writing binary representation (version 10) to passenger.mod

$ semodule_package -o passenger.pp -m passenger.mod
```

### Install the SELinux Module
```
#!shell
semodule -i passenger.pp
```

### Restart Apache
```
#!shell
$ service httpd stop
Starting httpd:                                            [  OK  ]
```
