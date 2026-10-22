# IGMP Snooping Desligado

O IGMP Snooping permite ao switch entregar o tráfego multicast apenas aos dispositivos que o pediram. Sem ele, o switch inunda todas as portas, mesmo que os dispositivos não o tenham pedido.

## Configuração do Switch
- Enable IGMP Snooping: Desligado
- Unknown Multicast Drop: Desligado

![Configuração do Switch](01-gui-desligado.png)

## O Emissor (PC Fixo .138)
O PC Fixo enviou o tráfego multicast para o grupo `239.1.1.1`.

![Emissor a enviar](02-fixo-envia.png)

## O Observador (Portátil A .163)
O Portátil A apenas tinha o Wireshark ligado, sem ter pedido o grupo. No entanto, como o snooping está desligado, o switch inunda a rede e o Wireshark do A vê os pacotes.

![Wireshark do A](04-wireshark-163.png)

## O Recetor (Portátil B .164)
O Portátil B correu o comando no CMD e juntou-se ao grupo.

![CMD do B](03-cmd-163-recebe.png)

Como o snooping está desligado, o Wireshark do B também continua a ver o tráfego.

![Wireshark do B](05-wireshark-164.png)

## Conclusão
Com o IGMP Snooping desligado, o tráfego multicast é inundado por toda a rede. Tanto o Portátil A como o Portátil B recebem os dados, mesmo que o A não tenha feito o pedido. Isto representa um desperdício de largura de banda.
