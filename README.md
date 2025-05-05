<h1>
  Serviços de Redes de Computadores
</h1>

<br>


# **📦 Configuração de serviços de rede Dockerizados**  

**🚀 Um ambiente Docker completo com DNS (Bind9), DHCP (isc-dhcp-server), Samba, FTP (vsftpd), LDAP, Firewall (iptables) e NGINX, pronto para ser replicado em qualquer máquina.**  

---

## **📌 Visão Geral**  
Este projeto automatiza a implantação de um **servidor de rede completo** dentro de um container Docker, incluindo:  
- **DNS** (Bind9) para resolução de nomes.  
- **DHCP** (isc-dhcp-server) para distribuição automática de IPs.  
- **Samba** para compartilhamento de arquivos.  
- **FTP** (vsftpd) para transferência de arquivos.  
- **LDAP** para autenticação centralizada.  
- **Firewall** (iptables) para segurança básica.  
- **NGINX** para hospedagem web.  

Tudo isso é **empacotado em uma imagem Docker personalizada**, facilitando a execução em qualquer máquina com apenas **um comando**.  

---

## **⚙️ Pré-requisitos**  
- **Docker** instalado ([Guia de instalação](https://docs.docker.com/engine/install/))  
- **Docker Compose** (geralmente incluso na instalação do Docker)  
- **Linux** (recomendado) ou WSL2 no Windows  

---

## **🛠️ Como Usar**  

### **1️⃣ Clone o repositório (ou copie os arquivos necessários)**  
```bash
git clone https://github.com/seu-usuario/docker-network-services.git
cd docker-network-services
```

### **2️⃣ Construa a imagem Docker**  
```bash
docker-compose build
```

### **3️⃣ Inicie o container**  
```bash
docker-compose up -d
```

### **4️⃣ Acesse o container**  
```bash
docker exec -it debian-rede bash
```

---

## **📂 Estrutura do Projeto**  
```
.
├── Dockerfile            # Configuração da imagem Docker
├── docker-compose.yml    # Definição do container e rede
├── configs/             # (Opcional) Pasta para configurações personalizadas
│   ├── dhcpd.conf       # Configuração do DHCP
│   ├── named.conf.local # Configuração do DNS (Bind9)
│   └── smb.conf         # Configuração do Samba
└── README.md            # Este arquivo
```

---

## **🔧 Configurações Personalizáveis**  
Antes de construir a imagem, você pode editar:  
- **`Dockerfile`** → Adicione/remova pacotes conforme necessário.  
- **`docker-compose.yml`** → Ajuste a subnet (`192.168.1.0/24`) ou volumes.  
- **Arquivos em `configs/`** → Defina configurações específicas para DHCP, DNS, Samba, etc.  

---

## **Iniciando**  

```bash
### 🖼 Criação de Imagem com Docker

### 👨‍💻 Parte 1: Criando e Listando Contêineres

# Baixar a imagem Debian
bash
docker pull debian


# Verificar contêineres em execução
bash
docker ps


# Verificar todos os contêineres (em execução e parados)
bash
docker ps -a

```

---

## **📌 Colaboradores**  
<div>
  <h5>Paulo Martins Alves do Prado</h5>
  <p>
    Email: paulo.prado1@estudante.ifgoiano.edu.br
    <br>
    Github: https://github.com/PauloMAPrado
  </p>
</div>
<br>
<div>
  <h5>Sara Luiz de Farias</h5>
  <p>
    Email: sara.luiz@estudante.ifgoiano.edu.br
    <br>
    Github: https://github.com/saraafariass
  </p>
</div>

## **📌 Professor Orientador** 
<div>
  <h5>Roitier Campos Gonçalves</h5>
  <p>
    Email: roitier.goncalves@ifgoiano.edu.br
    <br>
    Github: https://github.com/Roitier
  </p>
</div>

---

### **🎯 Objetivo**  
O presente repositório tem por principal objetivo conter toda a documentação oficial do trabalho final da disciplina de Serviços de Redes de Computadores, oferecida pelo Instituto Federal Goiano - Campus Ceres durante o 5º período do curso de Sistemas de Informação, visando a apresentação e documentação como formas de obtenção de nota para aprovação na disciplina citada anteriormente.
