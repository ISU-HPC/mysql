# mysql

[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/937)

Please see https://www.hpc.iastate.edu/guides/containers/mysql-server for usage instructions.


## Quick Start

1. Make local directory structure for database information
```
$ mkdir -p ${PWD}/mysql/var/lib/mysql ${PWD}/mysql/run/mysqld
```

1. Download the sample .my.cnf and .mysqlpassword files
```
$ curl https://raw.githubusercontent.com/ISU-HPC/mysql/master/my.cnf > ${HOME}/.my.cnf
$ curl https://raw.githubusercontent.com/ISU-HPC/mysql/master/mysqlrootpw > ${HOME}/.mysqlrootpw
```    

1. Launch an instance of the container, bind-mounting the local directories
```
$ singularity instance.start --bind ${PWD}/mysql/var/lib/mysql/:/var/lib/mysql --bind ${PWD}/mysql/run/mysqld:/run/mysqld shub://ISU-HPC/mysql mysql
```

1. Run the container's runscript to initialize mysqld and then launch mysqld
```
$ singularity run instance://mysql
```

1. Verify mysqld is running by opening a shell in the container an starting the MySQL client
```
$ singularity shell instance://mysql
Singularity: Invoking an interactive shell within container...

bash: warning: setlocale: LC_ALL: cannot change locale (en_US.UTF-8)
Singularity ISU-HPC-mysql-master-latest.simg:~> mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 3
Server version: 5.7.21 MySQL Community Server (GPL)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

See https://www.hpc.iastate.edu/guides/containers/mysql-server for details on how to
connect to the `mysqld` server from outside the container, via both local socket
and the network.
