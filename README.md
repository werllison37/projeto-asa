# PROJETO FINAL DA DISCIPLINA ADMINISTRAÇÃO DE SISTEMAS ABERTOS

---

## 📌 **Objetivo do Projeto**
O projeto tem como objetivo criar um ambiente virtual que simula a operação de um provedor de internet e seus clientes. Os serviços são configurados utilizando **containers Docker**, permitindo o gerenciamento e escalabilidade dos sistemas.

A infraestrutura é composta por:
- **Provedor (barreta.com.br)**: Responsável por fornecer serviços como DNS e Proxy Reverso.
- **Cliente 1 (pirangi.com.br)**: Possui um servidor web WordPress com balanceamento de carga.
- **Cliente 2 (buzios.com.br)** (implementação futura).

---

## ⚙️ **Serviços Configurados**

### **E-mail - Postfix + Dovecot**

(Implementação parcial - Em andamento)

- Servidor de e-mail configurado com Postfix (SMTP) para envio de e-mails.
- Dovecot (IMAP/POP3) configurado para o recebimento de e-mails.
- Integração com autenticação segura via SSL/TLS.

### **Webmail - Roundcube**

(Implementação parcial - Em andamento)

- Interface web para acesso aos e-mails do provedor.
- Hospedado no container webmail, acessível via https://mail.barreta.com.br.
- Requer autenticação dos usuários cadastrados no serviço de e-mail.

### **DNS - Bind9**
- Gerencia a resolução de nomes para os domínios do provedor e dos clientes.

### **Proxy Reverso - Nginx**
- Funciona no container `proxy`, localizado no provedor (`barreta.com.br`).
- Redireciona requisições HTTPS para os clientes.

### **Servidor Web - WordPress (Cliente 1)**
- O cliente `pirangi.com.br` possui dois servidores WordPress (`web_pirangi` e `web_pirangi2`).
- O **Nginx no provedor** distribui as requisições entre os dois servidores.

### **Banco de Dados - MariaDB**
- Cada cliente tem seu próprio banco de dados MariaDB.
- Os bancos armazenam os dados dos sites WordPress.

### **SSH - Acesso Remoto Seguro**
- Implementado no `cliente 1` para acesso administrativo.
- **Root login desativado** para maior segurança.

---

## 🏗️ **Estrutura do Projeto**
```bash
📂 ASA-CLOUD/
│── 📂 Provedor/
│   ├── 📂 proxy/   # Configuração do Proxy Reverso
│   │   ├── nginx.conf
│   │   ├── Dockerfile
│   │   ├── Certificados SSL (barreta.crt, pirangi.crt, etc.)
│   │   ├── docker-compose.yml
│   ├── 📂 dns/     # Servidor DNS
│   │   ├── named.conf
│   │   ├── zonas/
│   │   ├── docker-compose.yml
│   ├── 📂 email/   # Servidor de e-mail (Postfix + Dovecot)
│   │   ├── dovecot.conf
│   │   ├── Dockerfile
│   │   ├── mail.cf
│   ├── 📂 webmail/ # Interface Webmail (Roundcube)
│   │   ├── config.inc.php
│   │   ├── Dockerfile
│
│── 📂 Cliente1/   # Cliente pirangi.com.br
│   ├── 📂 nginx/  # Configuração específica do cliente
│   ├── 📂 wordpress/  # Arquivos do WordPress
│   ├── 📂 mysql/   # Dados do Banco de Dados
│   ├── 📂 ssh/     # Servidor SSH do Cliente
│   ├── docker-compose.yml
│
│── 📂 Cliente2/   # Implementação futura (buzios.com.br)
│
└── README.md
```
---
## 📧 Contato:
E-mail: werllison.galvao@escolar.ifrn.edu.br