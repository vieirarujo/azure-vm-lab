# Criando uma Máquina Virtual Linux no Microsoft Azure

Este guia descreve o passo a passo para criar uma máquina virtual com Ubuntu Server no Microsoft Azure usando o portal web.

---

## ✅ Etapas

### 1. Acessar o Portal
- Acesse: [https://portal.azure.com](https://portal.azure.com)

### 2. Criar um Resource Group (opcional)
- Menu lateral > "Grupos de recursos" > "Criar"
- Nome: `lab-rg`
- Região: "Brasil Sul" ou outra próxima

### 3. Criar a Máquina Virtual
1. Menu lateral > "Máquinas virtuais" > "Criar"
2. Aba **Básico**:
   - Assinatura: (selecione a ativa)
   - Grupo de recursos: `lab-rg`
   - Nome da VM: `vm-linux-lab`
   - Região: Brasil Sul
   - Imagem: **Ubuntu Server 22.04 LTS**
   - Tamanho: **B1s** (uso gratuito)
   - Autenticação: **Chave SSH** ou **Senha**
   - Nome de usuário: `azureuser`
3. Aba **Disco**:
   - Tipo: Padrão HDD (para economia)
4. Aba **Rede**:
   - Criar nova VNet ou usar existente
   - Habilitar IP público
   - Criar NSG (grupo de segurança de rede) com porta **22** aberta
5. Clique em **Revisar + Criar** > **Criar**

### 4. Aguardar o Provisionamento

### 5. Conectar-se à VM
- Vá até "Máquinas virtuais" > `vm-linux-lab`
- Clique em **Conectar > SSH**
- Use o terminal:
```bash
ssh azureuser@<endereço-ip-público>
```

---

## 🔍 Verificação Inicial
Dentro da VM:
```bash
uname -a
sudo apt update && sudo apt upgrade -y
```

---

## 📆 Dicas
- Use `az vm list -o table` para listar as VMs via Azure CLI
- Crie snapshots antes de alterar algo crítico
- Apague recursos quando não estiver usando para evitar cobranças

---

Pronto! Sua máquina virtual Linux está ativa e pronta para uso. Documente comandos e configurações adicionais no diretório `dicas/`.
