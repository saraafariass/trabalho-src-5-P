# 🖧 Configuração do Servidor e Cliente DHCP usando Docker e Debian

# ------------------------------------------------------
# 🔧 Servidor DHCP
# ------------------------------------------------------

# 🐳 Inicia um contêiner Debian interativo com nome "debian-rede-dhcp"
docker run -it --name debian-rede-dhcp debian bash

# 🔄 Atualiza os repositórios de pacotes
apt update -y

# 🛠 Instala o editor de texto nano
apt install nano

# 🛠 Instala o servidor DHCP (isc-dhcp-server)
apt install -y isc-dhcp-server

# ⚙️ Abre o arquivo de configuração do DHCP (crie ou edite conforme necessário)
nano /etc/dhcp/dhcpd.conf

# ⚠️ Tenta instalar o systemctl (não funciona bem em contêineres, pode ser ignorado)
apt install systemctl

# ⚠️ Tenta reiniciar o serviço DHCP (pode falhar em contêiner sem systemd)
systemctl restart isc-dhcp-server

# 📄 (Opcional) Visualiza ou edita o arquivo de arrendamentos de IPs
nano /etc/dhcp/dhcpd.leases

# 🚀 Inicia o serviço DHCP de forma tradicional
service isc-dhcp-server start

# 📄 (Repetição, mas útil para verificar os leases)
nano /etc/dhcp/dhcpd.leases

# 🧭 Configura qual interface será usada pelo servidor DHCP
nano /etc/default/isc-dhcp-server
# (Adicione: INTERFACESv4="eth0")

# ✅ Testa a configuração do DHCP
dhcpd -t

# 📄 Visualiza o arquivo de leases do DHCP
nano /var/lib/dhcp/dhcpd.leases

# 🔁 Inicia novamente o serviço, se necessário
service isc-dhcp-server start

# 🛠 Edita novamente o arquivo principal de configuração, se necessário
nano /etc/dhcp/dhcpd.conf

# ❌ Encerra o contêiner
exit

# ------------------------------------------------------
# 💻 Cliente DHCP
# ------------------------------------------------------

# 🐳 Inicia um contêiner Debian interativo com nome "debian-rede-dhcp-cliente"
docker run -it --name debian-rede-dhcp-cliente debian bash

# 🔄 Atualiza os repositórios de pacotes
apt update             

# 🛠 Instala o cliente DHCP
apt install -y isc-dhcp-client

# ♻️ Libera o IP anterior da interface (substitua conforme necessário)
dhclient -r dd38c1eb6cd6

# 📡 Solicita um novo IP via DHCP
dhclient dd38c1eb6cd6
