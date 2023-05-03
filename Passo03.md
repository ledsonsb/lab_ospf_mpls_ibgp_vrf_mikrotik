## 1 - Ativando MPLS no Mikrotik

![Laborátorio completo](https://github.com/ledsonsb/lab_ospf_mpls_ibgp_vrf_mikrotik/blob/main/_imagens/passo01.PNG)

### Roteiro
* 
* Habilita o processo LDP MPLS passando os lsr-id e transport-address (ambos são a loopback)
* Adicionar quais interfaces físicas que irão participar do processo LDP MPLS

Habilita o protocolo MPLS
~~~cpp
mpls ldp set enabled=yes 
~~~
Adiciona o router-id
~~~cpp
lsr-id=172.16.0.4
~~~
habilita a loopback como transporte
~~~cpp
transport-address=172.16.0.4
~~~
Adiciona as interfaces  ao mpls
~~~cpp
mpls ldp interface add interface=ether1
mpls ldp interface add interface=ether2
~~~



##Não adiciona a loopback pois ja é a interface de transporte e router id###






