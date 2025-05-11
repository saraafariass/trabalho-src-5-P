### 🌐 Apache2 com Docker e Debian

### 👨‍💻 Parte 1: Servidor

# Criar contêiner Debian para o servidor Apache
```bash
docker run -it --name debian-rede-apache debian bash
```
# Baixar a imagem 
```bash
docker pull andyshinn/dnsmasq
```

# Atualizar pacotes
```bash
apt update -y
```

# Instalar o nano (editor de texto)
```bash
apt install nano
```

# Instalar o Apache2
```bash
apt install -y apache2
```

# Iniciar o serviço Apache2
```bash
service apache2 start
```

# Verificar o status do serviço Apache2
```bash
service apache2 status
```

# Remover o arquivo index.html padrão
```bash
rm /var/www/html/index.html
```

# Editar o arquivo index.html
```bash
nano /var/www/html/index.html
```

# Instalar net-tools (para ferramentas de rede)
```bash
apt install net-tools -y
```

# Instalar iproute2 (para manipulação de rede)
```bash
apt install iproute2 -y
```

# Verificar a configuração de rede
```bash
ip a
```

# Sair do contêiner
```bash
exit
```

# Documento HTML

```bash
<!DOCTYPE html>
<html>
<head>
    <title>Meu Servidor Apache</title>
</head>
<body>
    <h1>Servidor Apache Configurado com Sucesso!</h1>
</body>
</html>
```


