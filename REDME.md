 Projeto Prático: Testes de Força Bruta com Kali Linux + Medusa

Este projeto demonstra o uso da ferramenta **Medusa** para realizar testes controlados de força bruta em serviços vulneráveis, utilizando um ambiente isolado com **Kali Linux**, **Metasploitable 2** e **DVWA**.  
O objetivo é fins educacionais, de treinamento e estudo de medidas de mitigação.

---

## 📌 Objetivos do Projeto

- Configurar um ambiente de laboratório seguro no VirtualBox.
- Executar ataques simulados de:
  - Força bruta em **FTP**
  - Automação de login em formulário web (**DVWA**)
  - Password spraying em **SMB**
- Documentar wordlists, comandos e técnicas utilizadas.
- Apresentar recomendações de mitigação e hardening.

---

## 🧩 Arquitetura do Ambiente

### **Máquinas Virtuais**
| VM | Sistema | Finalidade |
|----|---------|------------|
| Kali Linux | Ferramenta ofensiva | Executar Medusa, enumeração, automação |
| Metasploitable 2 | Sistema vulnerável | FTP, SMB, DVWA, etc |

### **Configuração de Rede (VirtualBox)**

Ambas as VMs configuradas com:

- **Adaptador: em modo brigde**
- Permite comunicação direta com acesso à internet.

### **IPs utilizados (exemplo)**

- **Kali Linux:** `192.168.0.216`
- **Metasploitable 2:** `192.168.0.158`


   Medidas de Mitigação
1. Proteção contra força bruta

Fail2ban

Limite de tentativas

Bloqueio por IP

2. Políticas de senha

Complexidade

Frases-senha

Bloqueio de senhas fracas

3. Hardening de serviços

Substituir FTP por SFTP

Restringir SMB (mínimo necessário)

Atualizar serviços vulneráveis

4. Segurança em Aplicações Web

CAPTCHA

WAF (ModSecurity)

Proteção CSRF

5. Monitoramento

Logs

Alertas

SIEM
