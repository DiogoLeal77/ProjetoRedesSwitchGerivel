# ProjetoRedesSwitchGerivel

Projeto pessoal de redes e virtualização — switch gerível Zyxel GS1200-5 + servidor virtualizado.

## A ideia do projeto

A rede doméstica original é composta por dois switches não-geríveis. Isto significa que todos os dispositivos partilham a mesma rede e não existe qualquer controlo sobre o tráfego: não há segmentação, não há priorização, não há visibilidade.

Um switch não-gerível faz o básico — liga dispositivos entre si, e pronto. Toda a lógica que existe por trás de uma rede empresarial — VLANs, espelhamento de tráfego, priorização, agregação de ligações — fica escondida atrás de equipamento que não tem interface de gestão. Não se aprende a configurar aquilo que não se pode configurar.

Este projeto introduz um **switch gerível (Zyxel GS1200-5)** na rede, não para substituir os switches existentes, mas para **criar um segmento controlado** onde seja possível experimentar, medir e documentar aquilo que uma rede gerível permite fazer e uma rede doméstica comum não permite.

## O que foi feito (Fase 1 — Switch Gerível)

O projeto cobriu as seguintes funcionalidades e testes:

- **Acesso à interface web:** Configuração inicial e atribuição de um IP de gestão fixo.
- **Baseline:** Teste de conectividade base antes de qualquer alteração (ping, Advanced IP Scanner, Zenmap).
- **VLANs:** Criação de VLANs 10 e 20, isolamento de portas e confirmação de comunicação cruzada.
- **Port Mirroring:** Captura de tráfego de uma porta para outra, analisada com o Wireshark (ping e DNS).
- **QoS (Prioridade):** Atribuição de filas de prioridade (Queue 0 a 3) e prova prática do efeito do QoS com o `iperf3` e congestionamento controlado.
- **IGMP Snooping:** Controlo de tráfego multicast com e sem snooping, provando a entrega seletiva (usando `iperf 2`).

### Funcionalidades por implementar (Trabalho Futuro)
- **Rate Limit (Limitação de Largura de Banda):** O hardware atual não possui esta funcionalidade nativa na interface gráfica. Fica registado como trabalho futuro para exploração, juntamente com a **Link Aggregation** (que requer hardware com múltiplas portas de rede).

## O que se vai fazer (Fase 2 — Servidor virtualizado)

Correr uma máquina virtual Ubuntu Server num PC, com Docker a alojar três serviços de rede, acessíveis a partir de qualquer ponto da rede:

- **phpIPAM** — gestão de endereçamentos IP's
- **NetBox** — documentação da infraestrutura de rede
- **Zabbix** — monitorização e alertas

## O que este projeto demonstra

- Configuração de switch gerível (VLANs, mirroring, QoS, IGMP snooping)
- Análise de tráfego e protocolos com Wireshark (ICMP, DNS, IGMP)
- Medição de throughput e congestionamento com `iperf3` e `iperf 2`
- Testes de conectividade (Advanced IP Scanner, Zenmap)
- Virtualização com VirtualBox
- Serviços em Docker (phpIPAM, NetBox, Zabbix)
- Documentação técnica e histórico de progresso versionado no Git

## Ferramentas Usadas

- **Rede:** Zyxel GS1200-5, cabos Ethernet, Wireshark, Advanced IP Scanner, Zenmap, iperf 2, iperf3.
- **Servidores:** VirtualBox, Ubuntu Server, Docker, PuTTY (SSH).
- **Serviços:** phpIPAM, NetBox, Zabbix.
