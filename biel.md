Vamos explicar detalhadamente o que cada linha e configuração faz na sua rede:

### Configuração do Roteador

#### Interface FastEthernet0/0
```plaintext
enable
configure terminal
interface FastEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
```

1. **`enable`**: Entra no modo privilegiado do roteador.
2. **`configure terminal`**: Entra no modo de configuração global.
3. **`interface FastEthernet0/0`**: Entra na configuração da interface FastEthernet0/0.
4. **`ip address 192.168.1.1 255.255.255.0`**: Define o endereço IP da interface como 192.168.1.1 com a máscara de sub-rede 255.255.255.0.
5. **`no shutdown`**: Ativa a interface, garantindo que ela esteja operacional.
6. **`exit`**: Sai do modo de configuração da interface.

#### Configuração do Pool DHCP
```plaintext
ip dhcp pool LAN_POOL
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1
dns-server 192.168.1.2
exit
```

1. **`ip dhcp pool LAN_POOL`**: Cria um pool DHCP chamado "LAN_POOL".
2. **`network 192.168.1.0 255.255.255.0`**: Define a rede para a qual o pool DHCP fornecerá endereços IP, que é 192.168.1.0 com a máscara de sub-rede 255.255.255.0.
3. **`default-router 192.168.1.1`**: Define o gateway padrão (o roteador) para os dispositivos que obterem um endereço IP do DHCP.
4. **`dns-server 192.168.1.2`**: Define o servidor DNS para os dispositivos que obterem um endereço IP do DHCP (apontando para o servidor com IP 192.168.1.2).
5. **`exit`**: Sai do modo de configuração do pool DHCP.

### Configuração do Servidor

1. **IP estático: 192.168.1.2**
   - **Máscara de sub-rede**: 255.255.255.0
   - **Gateway padrão**: 192.168.1.1
   - Configura o servidor com um endereço IP estático, que não será atribuído pelo DHCP.

2. **DNS**
   - **Registro "www.trabalho.com" -> 192.168.1.2**: Configura o servidor DNS para resolver o nome de domínio `www.trabalho.com` para o endereço IP do servidor (`192.168.1.2`).

3. **HTTP**
   - Configura o servidor para hospedar uma página web, tornando-a acessível para os dispositivos na rede.

### Configuração dos PCs

1. **Configurar para obter IP via DHCP**:
   - Nos PCs, configure a interface de rede para obter um endereço IP automaticamente usando o DHCP.
   - Isso permite que os PCs obtenham endereços IP, gateway e servidores DNS do pool configurado no roteador.

### Resumo e Explicação

1. **Configuração do roteador**:
   - Configura a interface do roteador para atuar como o gateway da rede (192.168.1.1).
   - Cria um pool DHCP para fornecer endereços IP aos dispositivos na rede.

2. **Configuração do servidor**:
   - Define um IP estático para o servidor (192.168.1.2) para que ele não mude e sempre seja acessível pelo mesmo endereço.
   - Configura serviços de DNS e HTTP para que os PCs na rede possam resolver o domínio `www.trabalho.com` para o IP do servidor e acessar a página web hospedada no servidor.

3. **Configuração dos PCs**:
   - Configura os PCs para obter endereços IP dinamicamente via DHCP, simplificando a configuração e garantindo que eles possam acessar a internet e serviços na rede interna, como o servidor web.

Após estas configurações, os PCs na rede devem ser capazes de:
- Obter endereços IP automaticamente do roteador.
- Resolver o domínio `www.trabalho.com` para o endereço IP do servidor.
- Acessar a página web hospedada no servidor usando um navegador.
