## 1 - Fechar sessão iBGP entre os PEs para passar as VRFs

![Laborátorio completo](https://github.com/ledsonsb/lab_ospf_mpls_ibgp_vrf_mikrotik/blob/main/_imagens/passo01.PNG)

* De 64512 a 65535 são reservados para ASs privados
* Criar e ativar a instância iBGP apenas nos PES
* Número de AS
* Router-ID
* Fechar sessão com os peers
* Nome do peer remoto
* Endereço do peer remoto
* AS do peer remoto
* Address family VPN (para passar as VRFs)

Criar e ativar a instância BGP com seu router ID
~~~cpp
/routing bgp instance set default as=65501 router-id=172.16.0.4
~~~

Fechar sessão com os peers
Permitir trasporte vpnv4 (vrf)
~~~cpp
/routing bgp peer
add address-families=ip,vpnv4 name=PE3 remote-address=172.16.0.3 remote-as=\65001 ttl=default update-source=looopback
~~~


