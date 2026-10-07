# ProjetoRedesSwitchGerivel

Projeto pessoal de redes e virtualização — switch gerível Zyxel GS1200-5 + servidor virtualizado.

## A ideia do projeto

A rede doméstica original é composta por dois switches não-geríveis. Isto
significa que todos os dispositivos partilham a mesma rede e não existe
qualquer controlo sobre o tráfego: não há segmentação, não há priorização,
não há visibilidade.

Um switch não-gerível faz o básico — liga dispositivos entre si, e pronto.
Toda a lógica que existe por trás de uma rede empresarial — VLANs,
espelhamento de tráfego, priorização, agregação de ligações — fica escondida
atrás de equipamento que não tem interface de gestão. Não se aprende a
configurar aquilo que não se pode configurar.

Este projeto introduz um **switch gerível (Zyxel GS1200-5)** na rede, não
para substituir os switches existentes, mas para **criar um segmento
controlado** onde seja possível experimentar, medir e documentar aquilo que
uma rede gerível permite fazer e uma rede doméstica comum não permite.

## O que se vai fazer

O projeto está dividido em duas fases.

### Fase 1 — Switch gerível

Introduzir o switch gerível na rede e testar as funcionalidades que o
distinguem de um switch não-gerível:

- Acesso à interface web de gestão e configuração inicial
- Teste de conectividade base (ponto de referência antes de qualquer alteração)
- Segmentação com VLANs — isolar dispositivos na mesma rede física
- Port mirroring — duplicar tráfego para análise com Wireshark
- QoS — priorizar ou limitar largura de banda por porta
- Link aggregation (opcional) — agregar duas ligações numa só
- IGMP snooping (opcional) — controlar tráfego multicast

### Fase 2 — Servidor virtualizado

Correr uma máquina virtual Ubuntu Server num PC, com Docker a alojar três
serviços de rede, acessíveis a partir de qualquer ponto da rede:

- **phpIPAM** — gestão de endereçamentos IP's
- **NetBox** — documentação da infraestrutura de rede
- **Zabbix** — monitorização e alertas

## O que este projeto demonstra

- Configuração de switch gerível (VLANs, mirroring, QoS, LAG, IGMP)
- Análise de tráfego com Wireshark
- Medição de débito com iperf3
- Virtualização com VirtualBox
- Serviços em Docker
- Documentação técnica e histórico de progresso versionado
