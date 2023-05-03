## 2 - VLAN Router + MPLS

![Laborátorio completo](https://github.com/ledsonsb/lab_ospf_mpls_ibgp_vrf_mikrotik/blob/main/_imagens/passo02.PNG)

### Roteiro
* Adicionar 6 roteadores mikrotik
** Os CE1 e CE2 - Vermelhos e os CE1 e CE2 - azuis
** 2 roteadores serão transformados em switch (Todas interfaces em bridge para acesso apenas)
* Adicionar Vlans + IPs nos CEs e PEs

Comando para transformar o roteador em um switch/hub
~~~cpp
system identity set name=SwitchXingLing
interface bridge add name=bridge1
interface bridge port add interface=all bridge=bridge1 
~~~

#### Adicione as seguintes VLANs nos PEs 

Roteador PE2: 
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| loopback  |  172.16.0.2/32  |
|<sup>eth1</sup> | <sup>10.0.0.2/30</sup> |
| eth2  | 10.0.0.14/30  |
| **vlan10**  | **10.0.0.14/30**  |
| **vlan20**  | **10.0.0.14/30**  |

Roteador PE3: 
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| loopback  |  172.16.0.3/32  |
| eth1  | 10.0.0.6/30 |
| eth2  | 10.0.0.9/30  |

Comandos para adicionar IPs nas interfaces
~~~cpp
system identity set name=P1

interface bridge add name=loopback

ip address add address=172.16.0.1/32 interface=loopback
ip address add address=10.0.0.1/30 interface=ether1
ip address add address=10.0.0.5/30 interface=ether2
~~~
Subir o protocolo OSPF
~~~cpp
routing ospf instance set 0 router-id=172.16.0.1

routing ospf network add network=172.16.0.1 area=backbone
routing ospf network add network=10.0.0.0/30 area=backbone
routing ospf network add network=10.0.0.4/30 area=backbone
~~~
Verifica os vizinhos OSPF
~~~cpp
routing ospf neighbor print
~~~


(Comando para ser usado nos switchs)

tool romon set enabled=yes
(Apenas facilitar o acesso usando winbox nos labs)


