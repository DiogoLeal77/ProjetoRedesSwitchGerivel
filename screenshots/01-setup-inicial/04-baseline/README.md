# Teste de conectividade base

Antes de qualquer segmentação, foi confirmado que toda a rede está
visível e que cada dispositivo tem endereçamento atribuído pelo router.
Este é o ponto de referência contra o qual os testes seguintes (VLANs,
mirroring, QoS) vão ser comparados.

## Varredura da rede
fiz
O Advanced IP Scanner lista todos os dispositivos vivos da rede — o PC
fixo, os dois portáteis de teste, o switch gerível, o router, e os
restantes dispositivos domésticos. Confirma que a rede antiga e a nova
continuam a ser um único segmento alcançável.

![Scanner completo](05-scanner-rede.png)

## Endereçamento dos PCs

Ambos os PCs obtiveram endereço por DHCP a partir do router, confirmando
que o switch gerível está a comportar-se de forma transparente — a
encaminhar tráfego como qualquer switch não-gerível, sem qualquer
segmentação ativa.

**PC 1:**

![ipconfig PC 1](06-ipconfig-pc1.png)

**PC 2:**

![ipconfig PC 2](07-ipconfig-pc2.png)

## Nota

Os testes de ping entre dispositivos Windows não devolvem resposta
devido à configuração padrão do Windows Defender Firewall, que bloqueia
pedidos ICMP de entrada. Esta é uma limitação do sistema operativo, não
da rede — o Advanced IP Scanner e o endereçamento DHCP confirmam que
todos os dispositivos são alcançáveis ao nível da camada 2.

