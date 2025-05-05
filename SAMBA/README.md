### 🖧 SAMBA com Docker e Debian

### 👨‍💻 Parte 1: Servidor

# Criar contêiner Debian para o servidor Samba
```bash
docker run -it --name debian-rede-samba debian bash
```

# Atualizar pacotes
```bash
apt update
```

# Instalar nano e Samba
```bash
apt install nano -y
```
```bash
apt install samba -y
```

# Criar diretório compartilhado
```bash
mkdir -p /srv/samba/compartilhado
```

# Conceder permissões totais ao diretório compartilhado
```bash
chmod 777 /srv/samba/compartilhado
```

# Adicionar usuário para o Samba
```bash
adduser usuario1
```

# Editar configuração do Samba
```bash
nano /etc/samba/smb.conf
```

# Reiniciar serviço Samba
```bash
service smbd restart
```

# Verificar status do serviço Samba
```bash
service smbd status
```

# Instalar iproute2
```bash
apt install iproute2 -y
```

# Exibir interfaces de rede
```bash
ip a
```

# Verificar processos do Samba
```bash
ps aux | grep smbd
```

# Iniciar o serviço Samba
```bash
service smbd start
```

# Instalar netstat
```bash
apt install netstat -y
```

# Verificar portas e serviços do Samba
```bash
netstat -tulnp | grep smbd
```

# Sair do contêiner
```bash
exit
```

### 💻 Parte 2: Cliente

# Criar contêiner Debian para o cliente Samba
```bash
docker run -it --name debian-rede-samba-cliente debian bash
```

# Atualizar pacotes
```bash
apt update
```

# Instalar cliente SMB
```bash
apt install smbclient -y
```

# Listar compartilhamentos no servidor Samba
```bash
smbclient -L //172.17.0.2/ -U usuario1
```

# Sair do contêiner
```bash
exit
```