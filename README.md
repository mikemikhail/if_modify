# if_modify
NetConf script that checks on operational conditions, and pushes changes if needed

The script if_modify.py connects to an XR router (NETCONF YANG server), to check every few minutes on a couple of operational conditions.
If needed, one of two configuration changes is pushed and committed.

![Topology & conditions](https://github.com/mikemikhail/if_modify/blob/master/topology_conditions.png)
