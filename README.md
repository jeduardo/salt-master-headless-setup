# Salt Master headless setup

This repository contains the base files require to seed a simple Salt server
and its respective minion from scratch onto a remote machine that has yet
to receive a Salt configuration.

The only requirements for this are a working account in the target machine
(a root account in salt.winterhold.org is used for this example) and a local
instalation of salt-ssh (either apt-get install salt or brew install salt).

Before running this procedure it is also necessary to checkout the salt-formula,
added as a submodule of this repository. This can be accomplish with the following
commands:

```shell
git submodule init
git submodule update
```

Provided that the machine name is configured accordingly into `etc/salt/roster`, 
`srv/salt/top.sls` and `srv/pillar/top.sls`, all that is required to complete
the procedure is to execute the following command:

```shell
salt-ssh --log-file=./log/ssh \* state.highstate
```

The final result is a setup of a remote Salt master, and a Salt minion running
on the machine that is connected to the local master. 

The minion will not be automatically added to the master, and this has to be done
either from inside the master machine or through salt-ssh again, as below:

```shell
salt-ssh --log-file=./log/ssh \* 'cmd.run salt-key --A -y'
```

It is fine to target all machines with this command as long as the only one
configured in the roster is the master machine.  

The setup pillars can be reused as actual pillars for the Salt setup in the
continued operation.
