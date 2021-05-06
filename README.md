# Hello-world
Trying the tutorial Hello- World
I am new to git-hub so learning to use it


```
cd /opt/trex/v2.88
./t-rex-64 -i --iom 0
```
* where
    * `-i`: is to start trex-server in interective mode
    * `--iom`: defines the I/O mode. Can have - 0 (silent), 1 (normal), 2 (short) values.
    * other helpfull cmd args:
        * `-c`: defines the number of cpu cores for the trex-server. If not provided in
        the cmd argument, it is taken from the `trex_cfg.yml` which has a default value `1`.
        The number of cpus can be change also by modifying the `no_of_cpus` variable in the
        `host_vars`


1. Add your new node to the `trex-servers` or `devices-under-test` group in the inventory file
`hosts.yml`:

    ```
    all:
      hosts:
      children:
        trex-servers:
          hosts:
            ...
            my-new-trex-host.cob.bisdn.de:
        devices-under-test:
          hosts:
            my-devices-under-test.lab.bisdn.de:
    ```
2. Add appropriate configurations to the `host_vars` files according to the roles needed to be deployed on them (see roles/\*/defaults/main.yml).
        
	* `host_vars/podwhale5.bisdn.de.yml`: is an example config file for trex role
	* `host_vars/podwhale2.bisdn.de.yml`: is an example config file for dpdk role
