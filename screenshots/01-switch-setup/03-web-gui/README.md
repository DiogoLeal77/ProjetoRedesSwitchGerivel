\# Interface web de gestão



A interface web do switch gerível Zyxel GS1200-5 divide-se em oito

separadores, cada um responsável por uma área distinta de configuração ou

consulta. Abaixo está o que cada um permite fazer, com o respetivo

screenshot.



\## System



Informação geral do equipamento — modelo, firmware, uptime, endereço de

gestão, e estado atual de cada porta.



!\[Separador System](01-system.png)



\## Port



Configuração e estado das portas físicas — ativação, velocidade, flow

control, proteção contra broadcast storm e deteção de loops.



!\[Separador Port](02-port.png)



\## VLAN



Segmentação lógica da rede — PVID por porta, membros de cada VLAN, e

estado de cada porta em cada VLAN.



!\[Separador VLAN](03-vlan.png)



\## Link Aggregation



Agregação de duas portas numa única ligação lógica — para maior largura

de banda ou redundância.



!\[Separador Link Aggregation](04-link-aggregation.png)



\## Mirroring



Espelhamento de tráfego — cópia do tráfego de uma ou mais portas para uma

porta de monitorização, para captura e análise com Wireshark.



!\[Separador Mirroring](05-mirroring.png)



\## QoS



Priorização de tráfego — atribuição de cada porta a uma fila, com pesos

distintos, para controlar a ordem de processamento em caso de

congestionamento.



!\[Separador QoS](06-qos.png)



\## IGMP Snooping



Controlo de tráfego multicast — decide se o switch só entrega tráfego

multicast às portas que efetivamente pediram esse grupo, ou se o espalha

por todas.



!\[Separador IGMP Snooping](07-igmp-snooping.png)



\## Management



Configuração do próprio switch — endereço IP, gateway, password, VLAN de

gestão, timeout da sessão web, e opções de manutenção.



!\[Separador Management](08-management.png)

