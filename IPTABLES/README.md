### 🔒 IPTables com Docker e Debian

### 👨‍💻 Parte 1: Servidor

# Criar contêiner Debian para o servidor IPTables
```bash
docker run --privileged --name debian-rede-iptables1 -it debian bash
```

# Atualizar pacotes
```bash
apt update -y
```

# Instalar o nano (editor de texto)
```bash
apt install nano
```

# Instalar o iptables
```bash
apt install -y iptables
```

# Definir políticas padrão
```bash
iptables -P INPUT DROP
```
```bash
iptables -P OUTPUT ACCEPT
```

# Adicionar regras para aceitar conexões estabelecidas e relacionadas
```bash
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```

# Aceitar conexões na interface de loopback (localhost)
```bash
iptables -A INPUT -i lo -j ACCEPT
```

# Aceitar conexões na porta 22 (SSH)
```bash
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

# Aceitar conexões na porta 80 (HTTP)
```bash
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
```

# Aceitar conexões na porta 443 (HTTPS)
```bash
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
```

# Aceitar conexões na porta 389 (LDAP)
```bash
iptables -A INPUT -p tcp --dport 389 -j ACCEPT
```

# Instalar iptables-persistent para salvar as regras
```bash
apt update && apt install -y iptables-persistent
```

# Editar regras do iptables
```bash
nano /etc/iptables/rules.v4
```

# Verificar status do serviço iptables
```bash
service iptables status
```

# Sair do contêiner
```bash
exit
```