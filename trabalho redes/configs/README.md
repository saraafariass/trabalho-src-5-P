### 🖧 DHCP com Docker e Debian

### 👨‍💻 Parte 1: Servidor

# Criar contêiner Debian para o servidor DHCP
docker run -it --name debian-rede-dhcp debian bash

# Atualizar pacotes
apt update -y

# Instalar nano e DHCP Server
apt install nano -y
apt install isc-dhcp-server -y

# Editar configuração principal do DHCP
nano /etc/dhcp/dhcpd.conf

# Editar qual interface o servidor irá usar
nano /etc/default/isc-dhcp-server
# (ex: INTERFACESv4="eth0")

# Testar configuração
dhcpd -t

# Iniciar o serviço DHCP
service isc-dhcp-server start

# Verificar leases (concessões de IP)
nano /var/lib/dhcp/dhcpd.leases

# Sair do contêiner
exit

### 💻 Parte 2: Cliente

# Criar contêiner Debian para o cliente DHCP
docker run -it --name debian-rede-dhcp-cliente debian bash

# Atualizar pacotes
apt update -y

# Instalar cliente DHCP
apt install isc-dhcp-client -y

# Liberar IP antigo (substitua "eth0" se necessário)
dhclient -r eth0

# Solicitar novo IP via DHCP
dhclient eth0
