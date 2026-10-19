# IGMP Snooping Desligado

O IGMP Snooping permite ao switch saber quem quer receber tráfego multicast. Sem ele, o switch inunda todas as portas com o tráfego, mesmo que os dispositivos não o tenham pedido.

## Configuração do Switch
- Enable IGMP Snooping: Desligado
- Unknown Multicast Drop: Desligado

![Configuração do Switch](01-igmp-desligado.png)

## O Emissor (PC Fixo .138)
O PC Fixo foi configurado para enviar tráfego multicast para o grupo `239.1.1.1`.

![Emissor a enviar](02-fixo-envia.png)

## O Observador (Portátil B .164)
O Portátil B não pediu para entrar no grupo, mas como o Snooping está desligado, o switch inunda a rede e ele consegue ver todo o tráfego.

![Wireshark do B a ver o tráfego](03-b-ve-tudo.png)

## O Recetor Oficial (Portátil A .163)
O Portátil A juntou-se ao grupo e recebeu os dados.

![CMD do A a receber](04-a-recebe.png)

## Conclusão
Com o IGMP Snooping desligado, o tráfego multicast é entregue a todos os dispositivos da rede, mesmo aos que não o pediram. Isto representa um desperdício de largura de banda e um problema de segurança.
