### 📚 LDAP com Docker e Debian

### 👨‍💻 Parte 1: Servidor

# Criar contêiner Debian para o servidor LDAP
```bash
docker run -it --name debian-rede-ldap debian bash
```

# Atualizar pacotes
```bash
apt update -y
```

# Instalar o nano (editor de texto)
```bash
apt install nano
```

# Criar o arquivo de usuários usuarios.ldif
```bash
nano usuarios.ldif
```

# Instalar ferramentas LDAP
```bash
apt install ldap-utils -y
```

# Instalar pacote procps (para comandos como ps)
```bash
apt install procps -y
```

# Verificar o status do serviço slapd (LDAP daemon)
```bash
ps aux | grep slapd
```

# Realizar uma busca LDAP
```bash
ldapsearch -x -H ldap://172.17.0.2 -b dc=empresa,dc=local
```

# Iniciar o serviço slapd (LDAP)
```bash
/etc/init.d/slapd start
```

# Verificar o caminho do comando slapd
```bash
which slapd
```

# Instalar o servidor LDAP slapd
```bash
apt update && apt install slapd -y
```

# Adicionar entradas no LDAP a partir do arquivo usuarios.ldif
```bash
ldapadd -x -D "cn=admin,dc=empresa,dc=local" -W -f usuarios.ldif
```

# Reconfigurar o servidor LDAP
```bash
dpkg-reconfigure slapd
```

# Realizar a busca LDAP novamente
```bash
ldapsearch -x -H ldap://172.17.0.2 -b dc=empresa,dc=local
```

# Sair do contêiner
```bash
exit
```

# Documento LDAP

# usuarios.ldif

```bash                             
dn: ou=usuarios,dc=example,dc=com
objectClass: organizationalUnit
ou: usuarios

dn: uid=roitier,ou=usuarios,dc=example,dc=com
objectClass: inetOrgPerson
uid: roitier
sn: goncalves
cn: Roitier Goncalves
userPassword: 123456789

```
