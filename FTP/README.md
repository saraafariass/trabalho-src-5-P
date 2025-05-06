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

# Documento FTP

# /etc/vsftpd.conf

```bash
listen=YES
listen_ipv6=NO
anonymous_enable=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
```
