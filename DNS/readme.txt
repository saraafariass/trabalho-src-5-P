### 🖧 DNS com Docker e Debian

### 👨‍💻 Parte 1: Servidor

# Criar contêiner Debian para o servidor DNS
bash
docker run -it --name debian-rede-dns debian bash


# Atualizar pacotes
bash
apt update -y


# Instalar o Bind9 (servidor DNS) e utilitários de DNS
bash
apt install -y bind9 dnsutils


# Instalar o Bind9 novamente (se necessário)
bash
apt install bind9


# Instalar o nano (editor de texto)
bash
apt install nano


# Editar o arquivo de configuração do Bind9
bash
nano /etc/bind/named.conf.local


# Editar o arquivo de zona para a empresa
bash
nano /etc/bind/db.empresa.local


# Editar o arquivo de zona para o IP
bash
nano /etc/bind/db.192


# Testar a configuração do DNS
bash
dig @127.0.0.1 www.empresa.local


# Editar o arquivo de opções de configuração do Bind9
bash
nano /etc/named.conf.options


# Reiniciar o serviço Bind9
bash
service bind9 restart


# Sair do contêiner
bash
exit


### 💻 Parte 2: Cliente

# Criar contêiner Debian para o cliente DNS
bash
docker run -it --name debian-rede-dns-cliente debian bash


# Atualizar pacotes
bash
apt update -y


# Instalar o nano (editor de texto)
bash
apt install nano


# Editar o arquivo de configurações de DNS
bash
nano /etc/resolv.conf


# Instalar utilitário para testar a conectividade (ping)
bash
apt install iputils-ping


# Testar a resolução de DNS
bash
ping www.empresa.local


# Instalar o utilitário DNS
bash
apt install dnsutils


# Testar o DNS com o comando dig
bash
dig www.empresa.local @172.17.0.2


# Sair do contêiner
bash
exit
