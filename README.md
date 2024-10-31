# Configuração de Servidor DHCP no Windows Server 2016

Este projeto demonstra como configurar e testar um servidor DHCP no Windows Server 2016 para distribuir endereços IP automaticamente para dispositivos em uma rede local.

## Sumário
- [Requisitos](#requisitos)
- [Passo 1: Instalar a Função DHCP](#passo-1-instalar-a-função-dhcp)
- [Passo 2: Configurar o DHCP](#passo-2-configurar-o-dhcp)
- [Passo 3: Criar um Escopo DHCP](#passo-3-criar-um-escopo-dhcp)
- [Passo 4: Ativar o Escopo](#passo-4-ativar-o-escopo)
- [Passo 5: Testar o Servidor DHCP](#passo-5-testar-o-servidor-dhcp)

---

## Requisitos
- Windows Server 2016 com IP fixo.
- Acesso com permissões de administrador no servidor.

---

## Passo 1: Instalar a Função DHCP
1. Abra o **Server Manager** no Windows Server 2016.
2. Clique em **Add roles and features** (Adicionar funções e recursos).
3. No assistente de configuração, clique em **Next** até chegar à seleção de funções.
4. Marque a função **DHCP Server** e clique em **Next**.
5. Siga as próximas etapas e clique em **Install** para instalar a função DHCP.

---

## Passo 2: Configurar o DHCP
1. Após a instalação, vá até o **Server Manager** e clique na notificação de configuração pós-instalação do DHCP.
2. Clique em **Complete DHCP Configuration**.
3. No assistente, selecione a opção para autorizar o servidor DHCP no Active Directory, se aplicável.
4. Clique em **Commit** para completar a configuração.

---

## Passo 3: Criar um Escopo DHCP
1. No **Server Manager**, vá em **Tools > DHCP** para abrir o console DHCP.
2. Expanda o nome do servidor, clique com o botão direito em **IPv4** e selecione **New Scope** (Novo Escopo).
3. No assistente:
   - Defina o **Nome** e uma **Descrição** para o escopo.
   - Especifique a faixa de **Endereços IP** (inicial e final) para distribuir.
   - Defina a **Máscara de Sub-rede** e **Exclusões de IP**, se necessário.
   - Configure o **tempo de concessão** do IP (lease duration).
   - Configure outros parâmetros de rede, como **Gateway** e **DNS**, se aplicável.
4. Finalize o assistente para criar o escopo.

---

## Passo 4: Ativar o Escopo
1. No console DHCP, clique com o botão direito no escopo criado e selecione **Activate** (Ativar).

---

## Passo 5: Testar o Servidor DHCP
Para testar o servidor DHCP:
1. Configure um dispositivo cliente para obter um IP automaticamente.
   - No Windows 10, acesse **Configurações de Rede** > **Adaptador de Rede** > **Propriedades** do adaptador.
   - Selecione **Protocolo IP Versão 4 (TCP/IPv4)** e ative a opção **Obter um endereço IP automaticamente**.
2. Abra o **Prompt de Comando** no cliente e execute:
   ```bash
   ipconfig /release
   ipconfig /renew
3. Para verificar as configurações de IP, execute:
   ```bash
   ipconfig /all
  Certifique-se de que o Endereço IPv4 está dentro da faixa do escopo e o Servidor DHCP exibe o IP do servidor DHCP.
  
4. No console DHCP, vá até Address Leases para verificar se o cliente aparece na lista de concessões.

Este projeto fornece uma configuração básica de servidor DHCP para gerenciar a distribuição de IPs em uma rede local.
