# IGMP Snooping Ligado (A Prova)

O IGMP Snooping permite ao switch entregar o tráfego multicast **apenas** aos dispositivos que o pediram. Este teste prova a diferença de comportamento em relação ao teste anterior (Snooping Desligado).

## Configuração do Switch
- Enable IGMP Snooping: Ligado
- Unknown Multicast Drop: Desligado

![Configuração do Switch](01-gui-ligado.png)

## O Emissor (PC Fixo .138)
O PC Fixo enviou o tráfego multicast para o grupo `239.1.1.1`.

![Emissor a enviar](02-fixo-envia.png)

## O Recetor Oficial (Portátil A .163)
O Portátil A correu o comando no CMD e juntou-se ao grupo.

![CMD do A a receber](03-cmd-163-recebe.png)

## O Wireshark do Portátil A
Como o A pediu o grupo, o switch entregou-lhe o tráfego e o Wireshark dele encheu.

![Wireshark do A a receber](04-wireshark-163.png)

## O Observador Cortado (Portátil B .164)
O Portátil B tentou espiar o tráfego apenas com o Wireshark, sem pedir o grupo. Assim que o Portátil A fez o pedido, o switch **cortou-lhe o acesso**. O Wireshark do B ficou vazio.

![Wireshark do B vazio](05-wireshark-164.png)

## Conclusão
Com o Snooping ligado, o switch deixou de inundar a rede. O Portátil B, que não fez o pedido via CMD, deixou de receber os dados. Isto prova que o switch está a gerir o tráfego multicast de forma inteligente, entregando-o apenas a quem o pede.
