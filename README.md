Para configurar uma rede no Cisco Packet Tracer onde 10 computadores e um servidor estão conectados a um switch, que por sua vez está conectado a um roteador, e configurar o DHCP para os PCs adquirirem IP e acessarem uma página no servidor por DNS, siga estes passos:

### Passo 1: Configuração do Equipamento
1. *Adicionar dispositivos:*
   - Adicione um roteador (Router).
   - Adicione um switch (Switch).
   - Adicione 10 PCs.
   - Adicione um servidor (Server).

2. *Conectar os dispositivos:*
   - Conecte todos os PCs e o servidor ao switch usando cabos de rede.
   - Conecte o switch ao roteador.

### Passo 2: Configuração do Roteador
1. *Configurar interface do roteador:*
   - Acesse o roteador e entre no modo de configuração global:
     
     enable
     configure terminal
     interface FastEthernet0/0
     ip address 192.168.1.1 255.255.255.0
     no shutdown
     exit
     

2. *Configurar o DHCP no roteador:*
   - Configure o DHCP para fornecer endereços IP aos PCs:
     
     ip dhcp pool empresa
     network 192.168.1.0 255.255.255.0
     default-router 192.168.1.1
     dns-server 192.168.1.2
     exit
     

### Passo 3: Configuração do Servidor
1. *Configurar IP estático no servidor:*
   - Acesse a interface de configuração do servidor.
   - Configure o IP estático do servidor para 192.168.1.2, com máscara de sub-rede 255.255.255.0 e gateway 192.168.1.1.
   - Configure o DNS no servidor para 192.168.1.2.

2. *Configurar serviço DHCP no servidor:*
   - Acesse a aba de serviços e configure o DHCP se não configurado no roteador (opcional).

3. *Configurar serviço DNS no servidor:*
   - Acesse a aba de serviços e ative o serviço DNS.
   - Adicione um registro DNS para um domínio (por exemplo, "www.empresa.com") apontando para o IP do servidor (192.168.1.2).

4. *Configurar serviço HTTP no servidor:*
   - Acesse a aba de serviços e ative o serviço HTTP.
   - Crie uma página web simples que será servida aos PCs.

### Passo 4: Configuração dos PCs
1. *Configurar PCs para obter IP via DHCP:*
   - Para cada PC, acesse a configuração de rede e configure para obter IP automaticamente (via DHCP).

### Verificação
1. *Testar conectividade:*
   - Tente acessar o servidor web no navegador de cada PC usando o domínio configurado no DNS (por exemplo, http://www.empresa.com).

### Configuração Completa
Aqui está um resumo das configurações:

*Roteador:*

enable
configure terminal
interface FastEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

ip dhcp pool empresa
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1
dns-server 192.168.1.2
exit


*Servidor (configuração via GUI):*
- IP estático: 192.168.1.2
- DHCP: (se configurado aqui, faixa 192.168.1.3 a 192.168.1.254)
- DNS: Registro "www.empresa.com" -> 192.168.1.2
- HTTP: Página web configurada e ativa

*PCs:*
- Configurar para obter IP via DHCP.

### Resultado Esperado
Após essas configurações, os PCs devem obter um endereço IP automaticamente via DHCP, resolver o domínio configurado via DNS e acessar a página web no servidor.
