## 1 - Criar a rede de backbone e subir o OSPF

### Roteiro
* Adicionar 4 roteadores P1, PE2, PE3 e P4
* Adicionar os IPs das interfaces e as loopbacks
* Testar ping nos ips das interfaces
* Subir o protocolo de roteamento OSPF
* Criar a instância OSPF 
* Anunciar as redes para o OSPF

#### IPs das interfaces e as loopbacks

Roteador P1: 
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| loopback  |  172.16.0.1/32  |
| eth1  | 10.0.0.5/30 |
| eth2  | 10.0.0.1/30  |

Roteador PE2: 
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| loopback  |  172.16.0.2/32  |
| eth1  | 10.0.0.2/30 |
| eth2  | 10.0.0.14/30  |

Roteador PE3: 
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| loopback  |  172.16.0.3/32  |
| eth1  | 10.0.0.6/30 |
| eth2  | 10.0.0.9/30  |

Roteador P4: 
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| loopback  |  172.16.0.4/32  |
| eth1  | 10.0.0.13/30 |
| eth2  | 10.0.0.10/30  |

#### Comandos para adicionar IPs nas interfaces
~~~cpp
   system identity set name=P1

interface bridge add name=loopback
ip address add address=172.16.0.1/32 interface=loopback

ip address add address=10.0.0.1/30 interface=ether1

ip address add address=10.0.0.5/30 interface=ether2
~~~


