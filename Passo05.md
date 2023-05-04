# Configurações feitas nos PEs

Cria a VRF e associar a vlan
~~~cpp
add export-route-targets=65001:11 import-route-targets=65001:11 interfaces=vlan-vermelha route-distinguisher=65001:11 routing-mark=vermelha
~~~
Propaga as  VRFs no iBGP
~~~cpp
routing bgp instance vrf add routing-mark=vermelha redistribute-connected=yes redistribute-static=yes
~~~
Pingando usando a VRF
~~~cpp
 ping 100.64.1.2 routing-table=vermelha
~~~
