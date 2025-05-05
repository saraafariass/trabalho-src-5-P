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