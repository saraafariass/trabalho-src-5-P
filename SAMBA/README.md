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

# Documento SAMBA (Servidor)

# Documento /etc/samba/smb.conf
```bash
[global]
   workgroup = WORKGROUP
   server string = Servidor Samba
   netbios name = SAMBA-SERVER
   security = user
   map to guest = bad user
   dns proxy = no
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes
   log file = /var/log/samba/log.%m
   max log size = 1000
   logging = file
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:*>
   pam password change = yes
;   logon path = \\%N\profiles\%U
;   logon drive = H:
;   logon script = logon.cmd
; add user script = /usr/sbin/useradd --create-home %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account>
; add group script = /usr/sbin/addgroup --force-badname %g
;   include = /home/samba/etc/smb.conf.%m
;   idmap config * :              backend = tdb
;   idmap config * :              range   = 3000-7999
;   idmap config YOURDOMAINHERE : backend = tdb
;   idmap config YOURDOMAINHERE : range   = 100000-999999
;   template shell = /bin/bash
   usershare allow guests = yes

[homes]
   comment = Home Directories
   browseable = no
   read only = yes
   create mask = 0700
   directory mask = 0700
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/tmp
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @lpadmin

[shared]
   path = /srv/samba/compartilhado
   browsable = yes
   writable = yes
   read only = no
   guest ok = no
   valid users = usuario1

```
