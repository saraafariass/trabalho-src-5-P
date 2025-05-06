### 🖧 DHCP com Docker e Debian

### 👨‍💻 Parte 1: Servidor

# Criar contêiner Debian para o servidor DHCP
```bash
docker run -it --name debian-rede-dhcp debian bash
```

# Atualizar pacotes
```bash
apt update -y
```

# Instalar nano e DHCP Server
```bash
apt install nano -y
```
```bash
apt install isc-dhcp-server -y
```

# Editar configuração principal do DHCP
```bash
nano /etc/dhcp/dhcpd.conf
```

# Editar qual interface o servidor irá usar
```bash
nano /etc/default/isc-dhcp-server
```
# (ex: INTERFACESv4="eth0")

# Testar configuração
```bash
dhcpd -t
```

# Iniciar o serviço DHCP
```bash
service isc-dhcp-server start
```

# Verificar leases (concessões de IP)
```bash
nano /var/lib/dhcp/dhcpd.leases
```

# Sair do contêiner
```bash
exit
```

### 💻 Parte 2: Cliente

# Criar contêiner Debian para o cliente DHCP
```bash
docker run -it --name debian-rede-dhcp-cliente debian bash
```

# Atualizar pacotes
```bash
apt update -y
```

# Instalar cliente DHCP
```bash
apt install isc-dhcp-client -y
```

# Liberar IP antigo (substitua "eth0" se necessário)
```bash
dhclient -r eth0
```

# Solicitar novo IP via DHCP
```bash
dhclient eth0
```

# Documento /etc/dhcpd.conf

```bash
# Configura    o global
default-lease-time 600;
max-lease-time 7200;
authoritative;

# Sub-rede para clientes (192.168.2.0/24)
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.100 192.168.2.200;
  option routers 192.168.2.1;
  option subnet-mask 255.255.255.0;
  option domain-name-servers 192.168.1.10;
  option domain-name "empresa.local";
}

# Reservas fixas para servidores na rede 192.168.1.0/24
host dns-server {
  hardware ethernet 02:42:c0:a8:01:0a;
  fixed-address 192.168.1.10;
}
```

# Documento /etc/default/isc-dhcp-server

```bash
INTERFACESv4="eth0"
INTERFACESv6=""
```

# Documento /etc/dhcp/dhcpd.conf

```bash
# Configura    o global
default-lease-time 600;
max-lease-time 7200;
authoritative;

# Sub-rede para clientes (192.168.2.0/24)
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.100 192.168.2.200;
  option routers 192.168.2.1;
  option subnet-mask 255.255.255.0;
  option domain-name-servers 192.168.1.10;
  option domain-name "empresa.local";
}

# Reservas fixas para servidores na rede 192.168.1.0/24
host dns-server {
  hardware ethernet 02:42:c0:a8:01:0a;
  fixed-address 192.168.1.10;
}
```
