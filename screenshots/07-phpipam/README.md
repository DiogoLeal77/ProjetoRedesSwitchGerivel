# phpIPAM (Gestão de IPs)

O phpIPAM é uma aplicação web de código aberto para gestão de endereçamento IP (IPAM - IP Address Management). Permite documentar sub-redes, endereços IP utilizados e dispositivos da rede, evitando conflitos e facilitando a gestão da infraestrutura.

A aplicação foi instalada no servidor virtualizado (Ubuntu Server) através do Docker, utilizando o Docker Compose para orquestrar dois containers: um para a aplicação web e outro para a base de dados (MariaDB).

## Acesso ao Servidor e SSH (PuTTY)

A instalação do Docker foi feita remotamente a partir do PC Fixo, usando o PuTTY para aceder ao terminal do Ubuntu Server por SSH.

Configuração do PuTTY:
![PuTTY Config](01-putty-config.png)

Sessão SSH ligada com sucesso:
![PuTTY Login](02-putty-login.png)

## Evidências da Instalação

1. Ecrã de boas-vindas do instalador:
![Bem-vindo](03-phpipam-bem-vindo.png)

2. Escolha do tipo de instalação da base de dados:
![Tipo de BD](04-phpipam-tipo-bd.png)

3. Base de dados instalada com sucesso:
![BD Instalada](05-phpipam-bd-instalada.png)

4. Configuração pós-instalação (password e URL):
![Pós-instalação](06-phpipam-postinstall.png)

5. Dashboard final do phpIPAM (acessível via browser):
![Dashboard](07-phpipam-dashboard.png)

## Conclusão

O phpIPAM está acessível em http://192.168.1.169:8081 e o dashboard confirma a instalação bem-sucedida.
