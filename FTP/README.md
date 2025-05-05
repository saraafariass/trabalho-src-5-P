### 📡 FTP com Docker e Debian

### 👨‍💻 Parte 1: Servidor

# Criar contêiner Debian para o servidor FTP
```bash
docker run -it --name debian-rede-ftp debian bash
```

# Atualizar pacotes
```bash
apt update -y
```

# Instalar o nano (editor de texto)
```bash
apt install nano
```

# Instalar o vsftpd (servidor FTP)
```bash
apt install -y vsftpd
```

# Editar o arquivo de configuração do vsftpd
```bash
nano /etc/vsftpd.conf
```

# Iniciar o serviço vsftpd
```bash
service vsftpd start
```

# Verificar o status do serviço vsftpd
```bash
service vsftpd status
```

# Criar um usuário para o FTP
```bash
useradd ftpuser -m -s /bin/bash
```

# Definir senha para o usuário FTP
```bash
passwd ftpuser
```

# Reiniciar o serviço vsftpd
```bash
service vsftpd restart
```

# Verificar o serviço vsftpd
```bash
vsftpd /etc/vsftpd.conf
```

# Sair do contêiner
```bash
exit
```