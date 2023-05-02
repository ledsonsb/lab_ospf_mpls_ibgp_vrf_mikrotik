# OSPF + MPLS(LDP) + VRF

Um parágrafo da descrição do projeto vai aqui

### 📋 Pré-requisitos

Precisa ter o eve-ng com imagem do mikrotik já fuincionando para este laborátorio

* [Eve.ng](http://www.dropwizard.io/1.0.2/docs/) - O framework web usado
* [Link](https://maven.apache.org/) - Gerente de Dependência

```
Dar exemplos
```
O OSPF é um protocolo de roteamento dinâmico usado para encontrar o melhor caminho para transmitir o tráfego em uma rede. O MPLS com o LDP é uma tecnologia que utiliza etiquetas para tornar o encaminhamento de tráfego mais rápido e escalável. O VRF permite a criação de múltiplas instâncias de roteamento em um único dispositivo, mantendo separados os fluxos de tráfego entre diferentes redes, aumentando a segurança da rede. Em conjunto, essas tecnologias podem melhorar o desempenho, escalabilidade e segurança em ambientes de rede de grande porte.

![Laborátorio completo](https://github.com/ledsonsb/lab_ospf_mpls_ibgp_vrf_mikrotik/blob/main/_imagens/lab_completo.PNG)

### Passo 01 - Atribuição de IPs na interface e Backbone OSPF

![Backbone OSPF](https://github.com/ledsonsb/lab_ospf_mpls_ibgp_vrf_mikrotik/blob/main/_imagens/lab_completo.PNG)

CE – Customer Edge (Roteador do cliente)
LER/PE – Label Edge Router – Provider Edge (Roteadores de borda) Roteadores onde ligamos clientes
LR/P – Label Router – Provider (Core) - Roteadores onde não são ligados clientes

01.1 - Roteiro do passo 01

Adicionar 4 roteadores P1, PE2, PE3 e P4
Adicionar os IPs das interfaces e as loopbacks
Habilitar o Romon (Protocolo mikrotik Apenas facilitar o acesso usando winbox nos labs) 
tool romon set enabled=yes

“Pingar” nos ips da interfaces

P1
loopback: 172.16.0.1/32
eth1: 10.0.0.5/30
eth2: 10.0.0.1/30
PE2
loopback: 172.16.0.2/32
eth1: 10.0.0.2/30
eth2: 10.0.0.14/30
PE3
loopback: 172.16.0.3/32
eth1: 10.0.0.6/30
eth2: 10.0.0.9/30
P4
loopback: 172.16.0.4/32
eth1: 10.0.0.13/30
eth2: 10.0.0.10/30



