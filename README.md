# if_modify
NetConf script that checks on operational conditions, and pushes changes if needed

The script if_modify.py connects to an XR router (NETCONF YANG server), to check every few minutes on a couple of operational conditions.
If needed, one of two configuration changes is pushed and committed.

![Topology & conditions](https://github.com/mikemikhail/if_modify/blob/master/topology_conditions.png)

On the router, when a filure happens:

RP/0/RP0/CPU0:PE112#show ipv4 interface brief | include Up

Thu Jan 23 11:49:31.525 EST

Loopback0                      10.101.112.1    Up              Up       default 

Loopback55                     172.16.255.55   Up              Up       default 

Loopback425                    10.112.112.1    Up              Up       ARMY    

MgmtEth0/RP0/CPU0/0            172.16.7.112    Up              Up       default 

GigabitEthernet0/0/0/0         unassigned      Up              Up       default 

GigabitEthernet0/0/0/0.1112    10.100.12.12    Up              Up       default 

GigabitEthernet0/0/0/0.1212    10.100.21.12    Up              Up       default 

GigabitEthernet0/0/0/0.1412    10.112.1.12     Up              Up       JIE     

GigabitEthernet0/0/0/2         unassigned      Up              Up       default 

GigabitEthernet0/0/0/2.2801    10.21.12.1      Up              Up       default 

GigabitEthernet0/0/0/5         unassigned      Up              Up       default 

GigabitEthernet0/0/0/5.100     unassigned      Up              Up       default 

GigabitEthernet0/0/0/5.101     unassigned      Up              Up       default 

RP/0/RP0/CPU0:PE112#show isis topology 

Thu Jan 23 11:49:36.185 EST

IS-IS ISIS paths to IPv4 Unicast (Level-2) routers

System Id       Metric  Next-Hop        Interface       SNPA          

P101            **    

P102            12120   P102            Gi0/0/0/0.1212  *PtoP*        

PE112           --    

RP/0/RP0/CPU0:PE112#show configuration commit changes last 1 

Thu Jan 23 11:50:10.946 EST

Building configuration...

!! IOS XR Configuration version = 6.4.2

interface Loopback55

description ENABLED ONLY IF NEIGHBOR ADJACENCY FAILS 

ipv4 address 172.16.255.55 255.255.255.255

!

end
