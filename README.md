# 🛡️ Laboratório: Pentest em Ambiente Docker (Hardware Legado)

**Autor:** Marcos Freire  
**Status:** Concluído  
**Foco:** Infraestrutura, Docker, Linux Hardening e Web Security (OWASP).

---

## 🎯 Objetivo do Projeto
Demonstrar a viabilidade de execução de testes de intrusão modernos utilizando hardware reutilizado. O projeto consistiu em transformar um notebook antigo em um servidor de aplicações vulneráveis isolado via containers.

## 🏗️ Arquitetura do Lab

### 1. Servidor Alvo (Target) 🛡️
* **Hardware:** Notebook HP antigo (Recuperado).
* **Sistema Operacional:** Linux Mint XFCE (Otimizado para baixo consumo).
* **Tecnologia:** Docker Containers.
* **Aplicação:** DVWA (Damn Vulnerable Web App).

### 2. Máquina Atacante (Attacker) ⚔️
* **Hardware:** Lenovo IdeaPad S145.
* **Sistema Operacional:** Windows 11.
* **Ferramentas:** Navegador Web, Burp Suite (opcional).

---

## 🛠️ Implementação Técnica

### Passo 1: Preparação do Ambiente (Hardening)
O notebook HP apresentava limitações de hardware. Para contornar isso:
* Instalação limpa do **Linux Mint XFCE**.
* Configuração de rede estática para servir como "Servidor de Lab".
* Instalação e configuração do **Docker Engine** para isolar a aplicação do sistema principal.

### Passo 2: O Desafio de Conectividade
Durante o setup, identifiquei uma incompatibilidade no driver da placa Wi-Fi do Linux.
* **Solução:** Utilizei conexão via cabo (Ethernet) diretamente no roteador/switch para garantir estabilidade e baixa latência durante os ataques.

---

## 🚩 Prova de Conceito (PoC): SQL Injection

Com o ambiente rodando, realizei um ataque de **SQL Injection (SQLi)** a partir do notebook Lenovo contra o container no HP.

**Vetor de Ataque:**
* **Alvo:** Campo de busca de "User ID" do DVWA.
* **Vulnerabilidade:** Falha na sanitização de input do banco de dados.
* **Payload:** `' OR '1'='1`

**Resultado:**
A injeção foi bem-sucedida, retornando a lista completa de usuários e senhas (hashes) do banco de dados, confirmando a criticidade da falha.

## 🛡️ Como corrigir esta vulnerabilidade Para prevenir o SQL Injection demonstrado, a aplicação deve utilizar Prepared Statements (Consultas Parametrizadas). Isso garante que o input do usuário seja tratado apenas como dado, e não como parte do comando SQL executado pelo servidor.
---

## 🚀 Competências Demonstradas
* ✅ **Linux SysAdmin:** Gerenciamento de pacotes e serviços.
* ✅ **Docker:** Deploy de aplicações containerizadas.
* ✅ **Redes:** Configuração de interfaces e troubleshooting de conectividade.
* ✅ **Pentest Web:** Identificação e exploração de falhas OWASP Top 10.
