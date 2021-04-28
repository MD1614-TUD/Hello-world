# Hello-world
Trying the tutorial Hello- World
I am new to git-hub so learning to use it

## Adding drawings for test
- something
	- something more
		- <u>something</u> better flags: defines the vlan configuration flags for the VIDs in `vid`. This variable is a list of strings, each corresponding to a flag to add to the vlan configuration. See [Bridge_Vlan_flags](https://man7.org/linux/man-pages/man8/bridge.8.html#bridge_vlan_-_VLAN_filter_list) for all Roses are {: .gitlab-purple} **`y`**\*2X**`n`**G.

		- [test_relative_link](test_drawings/Podwhale_setup_spirent.png)

<h1>Readme check</h1>

I just love <p style="color: red;">bold text<p>

<font color="red">xxxorem Ipsum</font> 

<font style="color:#FF0000">This is some text!</font>

2X __`n`__ G

<font size="2"> your text </font>

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
