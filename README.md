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
> nmap -sV 192.168.170.129

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
> medusa -h 192.168.170.129 -U users.txt -P pass.txt -M ftp -t 6

**Parâmetros utilizados**
| Parâmetro | Função             |
| --------- | ------------------ |
| -h        | Host alvo          |
| -u        | Usuário            |
| -P        | Wordlist de senhas |
| -M        | Módulo do serviço  |
| -t        | Número tentativas  |  

Resultado esperado  
Caso a senha esteja presente na wordlist:  
> ACCOUNT FOUND: [ftp] Host: 192.168.170.129 User: msfadmin Password: msfadmin

Esse resultado demonstra como credenciais fracas podem ser facilmente comprometidas.

# 🌐 Teste de Autenticação Web (DVWA)

Para simulação de ataques contra aplicações web foi utilizado:

**DVWA**

Acesso à aplicação
> http://192.168.170.129/dvwa
Credenciais padrão:
> user: admin
password: password

Esse ambiente permite testar vulnerabilidades relacionadas a:
* autenticação fraca
* brute force em formulários web
* falhas de validação

# 🖥️ Password Spraying em SMB

Outro cenário testado foi o password spraying contra serviço SMB.

Esse tipo de ataque consiste em testar uma senha comum contra múltiplos usuários, evitando bloqueios por excesso de tentativas.

Enumeração de usuários

Ferramenta utilizada:
> enum4linux 192.168.170.129

Ataque com Medusa
>medusa -h 192.168.170.129 -U smb_users.txt -P senhas_spray.txt -M smbnt -t 2 -T 50
Esse ataque demonstra como senhas comuns podem comprometer diversas contas simultaneamente.

# 🛡️ Medidas de Mitigação

Para prevenir ataques de força bruta em ambientes reais, recomenda-se:
* Política de senhas fortes
* mínimo de 12 caracteres
* letras maiúsculas e minúsculas
* números e caracteres especiais
  
Autenticação multifator (MFA)
Adição de um segundo fator de autenticação.

**Bloqueio de tentativas de login**

Exemplo:
> Bloqueio após 5 tentativas falhas

**Monitoramento de logs**
Ferramentas recomendadas:
* Fail2Ban
* Wazuh

**Rate Limiting**
Limitar número de tentativas de autenticação por IP.

## ⚠️ Aviso Legal

Este projeto foi desenvolvido exclusivamente para fins educacionais em ambiente controlado de laboratório.

A execução de testes de segurança deve ser realizada somente em ambientes autorizados.

## 👨‍💻 Autor
Paulo Joabe Silva Almeida  
Analista de Suporte | Infraestrutura de TI | Redes  
Tecnologo em 






























