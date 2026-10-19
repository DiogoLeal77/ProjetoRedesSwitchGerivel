# IGMP Snooping Ligado (A Prova com Timestamps)

O IGMP Snooping permite ao switch entregar o tráfego multicast **apenas** aos dispositivos que o pediram. Este teste prova, com a hora exata (timestamps), a diferença de comportamento em relação ao teste anterior.

## Configuração do Switch
- Enable IGMP Snooping: Ligado
- Unknown Multicast Drop: Desligado

![Configuração do Switch](01-gui-ligado.png)

## O Emissor (PC Fixo .138)
O PC Fixo enviou o tráfego multicast para o grupo `239.1.1.1`.

![Emissor a enviar](02-fixo-envia.png)

## O Observador Cortado (Portátil A .163)
O Portátil A tentou espiar o tráfego apenas com o Wireshark, sem ter pedido o grupo via CMD. 

Se olharmos para a coluna do tempo (Time) no Wireshark do A, vemos que ele estava a receber os pacotes, mas **parou exatamente no segundo em que o Portátil B se juntou ao grupo** (às 18:15). A partir daí, o switch cortou-lhe o acesso.

![Wireshark do A cortado](04-wireshark-163.png)

## O Recetor (Portátil B .164)
O Portátil B correu o comando no CMD e juntou-se ao grupo.

![CMD do B](03-cmd-163-recebe.png)

Como o B pediu o grupo, o switch entregou-lhe o tráfego. O Wireshark do B continua a receber os pacotes.

![Wireshark do B](05-wireshark-164.png)

## Conclusão
Com o Snooping ligado, o switch deixou de inundar a rede. O Portátil A, que não fez o pedido, deixou de receber os dados no exato momento em que o B fez o seu pedido. Isto prova que o switch entrega o tráfego apenas a quem o pede.
