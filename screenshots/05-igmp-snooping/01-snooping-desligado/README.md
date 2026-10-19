# IGMP Snooping Desligado

O IGMP Snooping permite ao switch entregar o tráfego multicast apenas aos dispositivos que o pediram. Sem ele, o switch inunda todas as portas, mesmo que os dispositivos não o tenham pedido.

## Configuração do Switch
- Enable IGMP Snooping: Desligado
- Unknown Multicast Drop: Desligado

![Configuração do Switch](01-gui-desligado.png)

## O Emissor (PC Fixo .138)
O PC Fixo enviou o tráfego multicast para o grupo `239.1.1.1`.

![Emissor a enviar](02-fixo-envia.png)

## O Recetor Oficial (Portátil A .163)
O Portátil A correu o comando no CMD e juntou-se ao grupo.

![CMD do A a receber](03-cmd-163-recebe.png)

## O Wireshark do Portátil A
Como o switch está a inundar a rede, o Wireshark do A vê os pacotes.

![Wireshark do A a receber](04-wireshark-163.png)

## O Observador (Portátil B .164)
O Portátil B também vê o tráfego no Wireshark, **mesmo sem ter pedido o grupo**. Isto acontece porque o snooping está desligado e o switch entrega o tráfego a todos.

![Wireshark do B a receber](05-wireshark-164.png)

## Conclusão
Com o IGMP Snooping desligado, o tráfego multicast é inundado por toda a rede. O Portátil B, que não pediu o grupo, continua a receber os dados, o que representa um desperdício de largura de banda e um problema de segurança.
