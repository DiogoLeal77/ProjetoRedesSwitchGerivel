# phpIPAM (Gestão de IPs)

O phpIPAM é uma aplicação web de código aberto para gestão de endereçamento IP (IPAM - IP Address Management). Permite documentar sub-redes, endereços IP utilizados e dispositivos da rede, evitando conflitos de IPs e facilitando a gestão da infraestrutura.

A aplicação foi instalada no servidor virtualizado (Ubuntu Server) através do Docker, utilizando o Docker Compose para orquestrar dois containers: um para a aplicação web e outro para a base de dados (MariaDB).

## Acesso ao Servidor (SSH via PuTTY)
A instalação foi feita remotamente a partir do PC Fixo, usando o PuTTY para aceder ao terminal do Ubuntu Server através de SSH.

![PuTTY Config](01-putty-config.png)
![PuTTY Login](02-putty-login.png)

## Criação do Docker e Docker Compose

### Porquê o Docker?
Em vez de instalar o phpIPAM e a base de dados diretamente no Ubuntu (o que poderia gerar conflitos de versões e dependências), optou-se pelo Docker. O Docker permite empacotar cada aplicação com todas as suas dependências num "container" isolado. O Docker Compose é a ferramenta que lê um ficheiro de configuração e levanta vários containers ao mesmo tempo, ligando-os automaticamente numa rede virtual privada.

### Comandos de Instalação
Os comandos abaixo foram executados no terminal do Ubuntu (via SSH). O primeiro atualiza o sistema; o segundo instala o Docker, o Git e o plugin do Docker Compose; o terceiro ativa o serviço do Docker para arrancar com o sistema; e o quarto dá permissões ao utilizador para usar o Docker sem precisar de sudo.

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y docker.io docker-compose-v2 git
sudo systemctl enable --now docker
sudo usermod -aG docker $USER

Configuração do Container (docker-compose.yml)
O ficheiro docker-compose.yml foi criado na pasta ~/homelab/phpipam. Este ficheiro define a arquitetura do serviço, especificando as imagens, as portas, as variáveis de ambiente e os volumes de persistência.
services:
  phpipam-db:
    image: mariadb:10.11
    environment:
      MYSQL_ROOT_PASSWORD: rootpass
    volumes:
      - phpipam_db_data:/var/lib/mysql
    restart: unless-stopped

  phpipam-web:
    image: phpipam/phpipam-www:1.6
    ports:
      - "8081:80"
    environment:
      TZ: Europe/Lisbon
      IPAM_DATABASE_HOST: phpipam-db
      IPAM_DATABASE_USER: phpipam
      IPAM_DATABASE_PASS: phpipampass
      IPAM_DATABASE_NAME: phpipam
    depends_on:
      - phpipam-db
    restart: unless-stopped

volumes:
  phpipam_db_data:

Utilidade de cada bloco:
phpipam-db: Define o container da base de dados usando a imagem oficial do MariaDB. A diretiva volumes garante que os dados não são perdidos se o container for reiniciado.

phpipam-web: Define o container da aplicação web. A diretiva ports: "8081:80" mapeia a porta 80 interna do container para a porta 8081 do servidor virtualizado, permitindo o acesso a partir do browser do PC Fixo. A diretiva depends_on garante que a base de dados arranca antes da aplicação web.

volumes: Declara o volume para o Docker saber onde guardar os dados de forma persistente.

Arranque e Gestão dos Serviços
Para arrancar os containers em segundo plano, foi utilizado o comando docker compose up -d. Para verificar o estado dos containers e confirmar que estavam a correr, foi utilizado o comando docker compose ps.

bash
cd ~/homelab/phpipam
docker compose up -d
docker compose ps

(Durante o arranque, o Docker descarregou as imagens do MariaDB e do phpIPAM e criou a rede virtual entre eles).

Evidências da Instalação
O processo de instalação foi feito através do browser no PC Fixo, acedendo a http://192.168.1.169:8081.

Ecrã de boas-vindas do instalador:
https://03-phpipam-bem-vindo.png/

Escolha do tipo de instalação da base de dados:
https://04-phpipam-tipo-bd.png/

Base de dados instalada com sucesso:
https://05-phpipam-bd-instalada.png/

Configuração pós-instalação (password e URL):
https://06-phpipam-postinstall.png/

Dashboard final do phpIPAM:
https://07-phpipam-dashboard.png/


Conclusão
O phpIPAM está acessível em http://192.168.1.169:8081 e o dashboard confirma a instalação bem-sucedida. A utilização do Docker Compose simplificou o processo, permitindo levantar a aplicação e a base de dados com um único comando e garantindo o isolamento e a persistência dos dados.
