# Salt Master headless setup

This repository contains the base files require to seed a simple Salt server
and its respective minion from scratch onto a remote machine that has yet
to receive a Salt configuration.

The only requirements for this are a working account in the target machine
(a root account in salt.winterhold.org is used for this example) and a local
instalation of salt-ssh (either apt-get install salt or brew install salt).

The final result is a setup of a remote Salt master, and a Salt minion running
on the machine that is connected to the local master. 

The setup pillars can be reused as actual pillars for the Salt setup in the
continued operation.
