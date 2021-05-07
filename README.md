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


* <ins>Tags:</ins>
    * `trex`: All required tasks in this playbook to provision the trex role have this tag.
        * This tag can be used to deploy trex-server without deploying it as a systemd service.
        ```
        ansible-playbook -l my-trex-host.cob.bisdn.de -i hosts.yml site.yml --tags "trex"
        ```
        * This tag can be skipped if trex role is already deployed in the target machine and
          the intention is to just have changes in trex service files systemd calls.

        ```
        ansible-playbook -l my-trex-host.cob.bisdn.de -i hosts.yml site.yml --skip-tags "trex" --tags "systemd_start_trex"
        ```
    * `systemd`: Tasks that interact with systemd (e.g. by calling systemctl) have this tag;
       You might wanna skip this tag when testing/developing in a docker container, e.g
    ```
    ansible-playbook -l my-trex-host.cob.bisdn.de -i hosts.yml site.yml --tags "systemd"
    ```
    * `systemd_start_trex`: Use this tag to trigger start of the trex-server.service, e.g.

    ```
    ansible-playbook -l my-trex-host.cob.bisdn.de -i hosts.yml site.yml --tags "systemd_start_trex"
    ```
    * `systemd_restart_trex`: Use this tag to trigger restart of the trex-server.service, e.g.
    ```
    ansible-playbook -l my-trex-host.cob.bisdn.de -i hosts.yml site.yml --tags "systemd_restart_trex"
    ```
    * `systemd_stop_trex`: Use this tag to stop the trex-server.service, e.g.
    ```
    ansible-playbook -l my-trex-host.cob.bisdn.de -i hosts.yml site.yml --tags "systemd_stop_trex"
    ```

