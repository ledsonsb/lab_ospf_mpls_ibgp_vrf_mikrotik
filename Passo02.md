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

### Tabela em HTML

<table class="table">
	<caption>PE2</caption>
	<thead>
	<tr>
		<th>Interface</th>
		<th>Address/Mask</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<td>loopback</td>
		<td>172.16.0.2/32</td>
	</tr>
	<tr>
		<td>eth01<br>
		<td>10.0.0.2/30<br>
	</tr>
	<tr>
		<td>eth02</td>
		<td>10.0.0.14/30</td>
	</tr>
		<tr>
		<th>
			eth03<br><strong>vlan10</strong><br><strong>vlan20</strong>
		</th>
		<th>
			-<br>100.64.1.1/30<br>100.64.2.1/30
		</th>
	</tr>
	</tbody>
</table>


<table class="table">
	<caption>PE3</caption>
	<thead>
	<tr>
		<th>Interface</th>
		<th>Address/Mask</th>
	</tr>
	</thead>
	<tbody>
	<tr>
		<td>loopback</td>
		<td>172.16.0.3/32</td>
	</tr>
	<tr>
		<td>eth01<br>
		<td>10.0.0.6/30<br>
	</tr>
	<tr>
		<td>eth02</td>
		<td>10.0.0.9/30</td>
	</tr>
		<tr>
		<th>
			eth03<br><strong>vlan10</strong><br><strong>vlan20</strong>
		</th>
		<th>
			-<br>100.64.4.1/30<br>100.64.3.1/30
		</th>
	</tr>
	</tbody>
</table>

CE01 - Vermelho
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| eth1-vlan10  | 10.0.0.2/30 |

CE02 - Vermelho 
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| eth1-vlan10  | 10.0.0.2/30 |

CE01 - Azul
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| eth1-vlan10  | 10.0.0.2/30 |

CE02 - Azul 
| INTERFACE | IP/MASK |
| ------------- | ------------- |
| eth1-vlan10  | 10.0.0.2/30 |

Comandos para adicionar Vlans nas interfaces do mikrotik
~~~cpp
interface vlan add vlan-id=10 name=vlanazul interface=ether3

ip address add address=100.64.3.1/30 interface=vlanverm
~~~



