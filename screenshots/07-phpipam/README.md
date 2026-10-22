# phpIPAM (Gestão de IPs)

O phpIPAM é uma aplicação web de código aberto para gestão de endereçamento IP (IPAM). Permite documentar sub-redes, endereços IP e dispositivos da rede, evitando conflitos.

A aplicação foi instalada no servidor virtualizado (Ubuntu Server) através do Docker, utilizando o Docker Compose para orquestrar dois containers: um para a aplicação web e outro para a base de dados (MariaDB).

## Acesso ao Servidor e SSH (PuTTY)

A instalação foi feita remotamente a partir do PC Fixo, usando o PuTTY para aceder ao terminal do Ubuntu Server por SSH.

Configuração do PuTTY:
![PuTTY Config](01-putty-config.png)

Sessão SSH ligada com sucesso:
![PuTTY Login](02-putty-login.png)

## A Lógica do Docker e do Docker Compose

Em vez de instalar o phpIPAM e a base de dados diretamente no Ubuntu (o que poderia gerar conflitos de versões), usámos o Docker. 

O Docker permite empacotar a aplicação e todas as suas dependências num "container" isolado. O Docker Compose é a ferramenta que lê o ficheiro de configuração e levanta os dois containers ao mesmo tempo, ligando-os numa rede virtual privada.

Para instalar o motor do Docker e o Docker Compose, foram executados os seguintes comandos:

sudo apt update && sudo apt upgrade -y
sudo apt install -y docker.io docker-compose-v2 git
sudo systemctl enable --now docker
sudo usermod -aG docker $USER

## Configuração e Comandos do Serviço

O ficheiro docker-compose.yml foi criado na pasta ~/homelab/phpipam. As diretivas mais importantes deste ficheiro são:

- image: Define a imagem oficial do phpIPAM e do MariaDB.
- ports: "8081:80": Mapeia a porta 80 do container para a porta 8081 do servidor. É por isso que acedemos no browser através do IP do servidor e da porta 8081.
- volumes: Garante que os dados da base de dados são guardados num disco virtual, sobrevivendo mesmo que o container seja reiniciado.
- depends_on: Garante que a base de dados arranca primeiro do que a aplicação web.

Para arrancar e verificar o estado dos containers, foram usados estes comandos:

cd ~/homelab/phpipam
docker compose up -d
docker compose ps

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
