# Port Mirroring

O port mirroring permite que um dispositivo veja todo o tráfego de uma
porta específica do switch, sem fazer parte dessa comunicação. Esta
funcionalidade é a base de ferramentas de monitorização, análise de
tráfego e deteção de intrusões.

## Configuração aplicada

O switch gerível foi configurado para espelhar todo o tráfego da porta 4
para a porta 2:

- **Mirrored Port:** porta 4 (PC que gera o tráfego)
- **Monitor Port:** porta 2 (PC que captura com Wireshark)
- **Direction:** Both (entrada e saída)

![Configuração do mirroring](02-mirror-config.png)

## Testes realizados

Foram feitos testes para validar o funcionamento do port mirroring,
documentados em pastas separadas:

1. **Teste de ICMP (ping):** captura de tráfego de ping, confirmando que
o PC monitor recebe as cópias dos pacotes enviados pelo PC espelhado.
