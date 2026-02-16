# Rede de Escritório Regional - Simulação Cisco Packet Tracer

Desenvolvido como parte do meu portfólio de Redes, este repositório contém uma simulação de rede para um ambiente de escritório regional projetada no **Cisco Packet Tracer**. O projeto foca em conceitos fundamentais de rede, incluindo serviços DHCP, conectividade dual-stack IPv4/IPv6 e o endurecimento (hardening) essencial de dispositivos.

## 🚀 Principais Recursos e Tecnologias

* **Roteamento Dual-Stack (IPv4 e IPv6):** Implementação de ambas as famílias de endereços para garantir conectividade moderna.
* **Configuração de Servidor DHCP:** O roteador `Office-Router` atua como o servidor DHCP para a rede local (Pool: "office"), fornecendo endereçamento automático aos dispositivos finais.
* **Segurança e Hardening de Rede:**
    * **Segurança de Gerenciamento:** Senhas criptografadas (`service password-encryption`) e senha secreta de enable.
    * **Acesso Remoto:** SSH configurado para gerenciamento remoto seguro, desativando o Telnet inseguro.
    * **Segurança de Portas:** Todas as portas FastEthernet e Gigabit não utilizadas no switch foram desativadas administrativamente (`shutdown`) para evitar acesso físico não autorizado.
    * **Banner MOTD:** Banner de aviso legal configurado para desencorajar acessos não autorizados.
    * **Servidor DNS:** Um servidor DNS personalizado para habilitar o SSH, proporcionar mais velocidade à rede e segurança mais granular.

## 📊 Tabela de Endereçamento

| Dispositivo | Interface | Endereço IPv4 | Endereço IPv6 | Descrição |
| :--- | :--- | :--- | :--- | :--- |
| **Office-Router** | G0/0 | DHCP (Internet) | 2000:DB8:ACAD:A::1/64 | Interface WAN |
| **Office-Router** | G0/1 | 192.168.1.1/24 | 2000:DB8:ACAD:B::1/64 | Gateway da LAN |
| **Office-Router** | Lo0 | 10.255.255.1/32 | N/A | Interface Loopback |
| **Office-Switch** | VLAN 1 | 192.168.1.254/24 | N/A | IP de Gerenciamento |

## 🛠️ Destaques da Configuração

### Exclusões DHCP
Para evitar conflitos de IP com dispositivos estáticos (como o Switch e o Gateway), os seguintes endereços foram excluídos do pool DHCP:
* `192.168.1.1` (Roteador)
* `192.168.1.100` (Reservado)

### Práticas de Segurança
A configuração do switch demonstra uma postura de segurança proativa ao desligar as portas de `Fa0/3` a `Fa0/22`. Isso garante que ataques do tipo "plug-and-play" sejam mitigados dentro do escritório.

## 📂 Estrutura do Repositório

* `configs/`: Arquivos `.txt` brutos contendo a saída do comando `show running-config` do Roteador e do Switch.
* `img/`: Capturas de tela da topologia e testes de conectividade bem-sucedidos (Pings/Navegador Web).
