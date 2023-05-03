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
| loopback   |  172.16.0.2/32  |
| eth1 | 10.0.0.2/30 |
| eth2  | 10.0.0.14/30  |
| **vlan10**  | **10.0.0.14/30**  |
| **vlan20**  | **10.0.0.14/30**  |

Roteador PE3: 
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| loopback **vlan10**  |  172.16.0.3/32 100.64.0.10/30  |
| eth1| 10.0.0.6/30 |
| eth2  | 10.0.0.9/30  |

### Tabela em HTML

<style>
	.demo {
		border:1px sólido #C0C0C0;
		border-collapse:colapso;
		padding:5px;
	}
	.demo th {
		border:1px sólido #C0C0C0;
		padding:5px;
		background:#F0F0F0;
	}
	.demo td {
		border:1px sólido #C0C0C0;
		padding:5px;
	}
</style>
<table class="demo">
	<caption>tabela 1</caption>
	<thead>
	<tr>
		<th>Cabeçalho 1</th>
		<th>Cabeçalho 2</th>
		<th>Cabeçalho 3</th>
		<th>Cabeçalho 4</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
	</tr>
	<tr>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
	</tr>
	<tr>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
	</tr>
	<tr>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
		<td>&nbsp;</td>
	</tr>
	</tbody>
</table>

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


