```markdown
# 🔍 Siaudi - Sistema de Auditoria

Sistema de auditoria desenvolvido originalmente pelo
[Software Público Brasileiro](https://softwarepublico.gov.br/social/siaudi/)
Este repositório contém a versão atualizada e compatível com ambientes modernos,
com correções de compatibilidade para PHP 8.1+ e stack tecnológica atual.

## 🚀 Status do Projeto

**✅ FUNCIONAL** - Compatível com versões modernas da stack LAMP
**🔧 MANUTENÇÃO ATIVA** - Corrigidas incompatibilidades de versões antigas

## 🎯 Objetivo

O Siaudi é um sistema completo de auditoria desenvolvido para organizações públicas, proporcionando controle e gestão de processos auditoriais com segurança e eficiência.

## ⚙️ Stack Tecnológica

| Componente | Versão | Descrição |
|------------|--------|-----------|
| **Backend** | PHP 8.1+ | Linguagem principal do sistema |
| **Banco de Dados** | PostgreSQL 12+ | SGBD relacional para dados auditoriais |
| **Servidor Web** | Apache 2.4 | Servidor HTTP com mod_rewrite |
| **Sistema Operacional** | Ubuntu 22.04 LTS | Ambiente de produção recomendado |

## 📋 Pré-requisitos

- Ubuntu 22.04 LTS (ou distribuição similar)
- Apache 2.4+
- PHP 8.1+
- PostgreSQL 12+
- 2GB RAM mínimo
- 20GB de espaço em disco

## 🛠 Instalação

### 1. Configuração do Ambiente Ubuntu

```bash
# Atualizar sistema
sudo apt update && sudo apt upgrade -y

# Instalar Apache
sudo apt install apache2 -y

# Ativar módulos necessários
sudo a2enmod rewrite
```

2. Configuração do Apache

```bash
# Editar configuração principal
sudo nano /etc/apache2/apache2.conf

# Alterar de:
# AllowOverride None
# Para:
# AllowOverride All

# Configurar document root
sudo nano /etc/apache2/sites-available/000-default.conf
# Alterar para: DocumentRoot /var/www/
```

3. Instalação do PHP e Dependências

```bash
sudo apt install php libapache2-mod-php php-pgsql php-gd php-mbstring php-curl php-xml php-zip php-cli -y
```

4. Configuração do PHP (php.ini)

```ini
session.auto_start = 1
error_reporting = E_ALL & ~E_DEPRECATED & ~E_STRICT & ~E_NOTICE
memory_limit = 1024M
post_max_size = 128M
display_errors = On
short_open_tag = On
```

5. Instalação do PostgreSQL

```bash
sudo apt install postgresql postgresql-contrib -y
```

6. Deploy da Aplicação

```bash
# Copiar projeto
sudo cp siaudi2 /var/www/

# Configurar permissões
sudo chown -R www-data:www-data /var/www/siaudi2
sudo chmod -R 755 /var/www/siaudi2

# Reiniciar Apache
sudo systemctl restart apache2
```

🗄 Configuração do Banco de Dados

1. Configuração de Localidade

```bash
sudo nano /etc/profile
# Adicionar: export LANG=pt_BR.UTF-8

sudo locale-gen pt_BR.UTF-8
source /etc/profile
sudo systemctl restart postgresql
```

2. Criação do Banco

```bash
sudo -u postgres psql -f /var/www/siaudi2/script_Bd/siaudispb.sql
```

3. Configuração de Conexão

Editar /var/www/siaudi2/protected/config/main.php:

```php
'db' => array(
    'class' => 'application.components.MyDbConnection',
    'connectionString' => 'pgsql:host=localhost;port=5432;dbname=bd_siaudi',
    'username' => 'usrsiaudi',
    'password' => '!@#-usr-siaudi',
    'charset' => 'UTF-8',
),
```

👤 Acesso ao Sistema

URL: http://localhost/siaudi2
Usuário: siaudi.gerente
Senha: 123456

🔧 Características Técnicas

✅ Corrigidas e Implementadas

· Compatibilidade com PHP 8.1+
· Configuração Apache otimizada
· Suporte ao PostgreSQL atualizado
· Locale pt_BR.UTF-8 configurado
· Permissões de sistema corrigidas

🎯 Funcionalidades Principais

· Gestão de processos auditoriais
· Controle de usuários e permissões
· Relatórios e documentação
· Workflows de auditoria
· Interface web responsiva

📁 Estrutura do Projeto

```
siaudi2/
├── protected/
│   ├── config/
│   │   └── main.php          # Configurações principais
│   └── components/
├── script_Bd/
│   └── siaudispb.sql         # Script do banco de dados
├── assets/                   # Arquivos estáticos
└── index.php                # Entry point
```

🐛 Solução de Problemas

Porta do PostgreSQL

Verifique a porta em uso:

```bash
sudo nano /etc/postgresql/12/main/postgresql.conf
# Verificar linha: port = 5432
```

Permissões

Caso tenha erro de permissões:

```bash
sudo chown -R www-data:www-data /var/www/siaudi2
sudo chmod -R 755 /var/www/siaudi2
```

🤝 Contribuições

Este projeto é uma versão atualizada do sistema original. Contribuições para:

· Melhoria de segurança
· Novas funcionalidades
· Correção de bugs
· Documentação

São sempre bem-vindas!

📄 Licença

Desenvolvido originalmente sob a licença do Software Público Brasileiro.

👨‍💻 Desenvolvedor

Walter Matheus

· Atualização e compatibilidade com stack moderna
· Correção de incompatibilidades PHP 8.1+
· Configuração de ambiente e documentação

---

⭐ Se este projeto foi útil, considere dar uma estrela no repositório!

```

---
