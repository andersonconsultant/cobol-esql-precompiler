# 🏗️ Cobol ESQL Precompiler – OCESQL

**OCESQL** (Open COBOL Embedded SQL) é um pré-compilador que permite a integração entre programas **COBOL** e comandos **SQL** utilizando **PostgreSQL**. Ideal para modernizar sistemas legados e facilitar a conexão com bancos de dados relacionais.

> Este projeto é baseado no `Open-COBOL-ESQL-1.4`, mantido por Tokyo System House Co., Ltd.

## ✨ Recursos
- Suporte a PostgreSQL 16
- Compatível com GnuCOBOL 3.1.2
- Instalação guiada para Ubuntu
- Pré-compilação simples com o comando `ocesql`

# 📘 Open-COBOL-ESQL-1.4 Installation Guide (Ubuntu)

Este guia detalha o processo completo para instalar e configurar o Open-COBOL-ESQL-1.4 em sistemas Ubuntu, incluindo todas as dependências e ajustes necessários antes de executar os comandos `./configure`, `make` e `make install`.

Recomendamos copiar a pasta "Open-COBOL-ESQL-1.4/" para a pasta home:
~/Open-COBOL-ESQL-1.4
ou home/seuusuário/Open-COBOL-ESQL-1.4
e executar os comandos abaixo a partir dela.

---

## ✅ Etapa 1: Preparar o Ambiente para ./configure

### 1. Atualizar os Repositórios

```bash
sudo apt update
```

### 2. Instalar PostgreSQL 16 e Bibliotecas de Desenvolvimento

```bash
sudo apt install postgresql-16 postgresql-client-16 libpq-dev
```

**Verificações:**
```bash
pkg-config --modversion libpq   # Esperado: 16.9
psql --version
```

### 3. Instalar GnuCOBOL 3.1.2

**A) Via Pacote (se disponível):**
```bash
sudo apt install gnucobol3
cobc --version   # Esperado: GnuCOBOL 3.1.2
```

**B) Via Fonte (caso não esteja disponível no repositório):**
```bash
wget https://sourceforge.net/projects/gnucobol/files/gnucobol/3.1/gnucobol-3.1.2.tar.gz
tar -xzf gnucobol-3.1.2.tar.gz
cd gnucobol-3.1.2
./configure
make
sudo make install
sudo ldconfig
export PATH=$PATH:/usr/local/bin
```

### 4. Instalar Ferramentas de Compilação e Dependências

```bash
sudo apt install build-essential libgmp-dev libdb-dev libncurses-dev autoconf automake libtool pkg-config
sudo apt install --reinstall pkg-config
sudo apt install bison flex
```

**Verificações:**
```bash
pkg-config --version     # Esperado: 1.8.1
autoconf --version       # Esperado: 2.72
automake --version       # Esperado: 1.16.5
bison --version          # Esperado: >= 3.x
flex --version           # Esperado: >= 2.x
which yacc               # Deve apontar para /usr/bin/bison ou similar
```

### 5. Configurar Variáveis de Ambiente

```bash
export CPPFLAGS="-I/usr/include/postgresql"
export LDFLAGS="-L/usr/lib/x86_64-linux-gnu"
export PKG_CONFIG_PATH="/usr/lib/x86_64-linux-gnu/pkgconfig:$PKG_CONFIG_PATH"
```

**Persistência no .bashrc:**
```bash
echo 'export PKG_CONFIG_PATH=/usr/lib/x86_64-linux-gnu/pkgconfig:$PKG_CONFIG_PATH' >> ~/.bashrc
echo 'export PATH=$PATH:/usr/local/bin' >> ~/.bashrc
source ~/.bashrc
```

### 6. Verificar libpq.pc e pkg.m4

```bash
find /usr -name libpq.pc         # Esperado: /usr/lib/x86_64-linux-gnu/pkgconfig/libpq.pc
find /usr -name pkg.m4           # Esperado: /usr/share/aclocal/pkg.m4
pkg-config --modversion libpq    # Esperado: 16.9
```

### 7. Corrigir o Script configure

Entre no diretório do Open-COBOL-ESQL:
```bash
cd ~/Open-COBOL-ESQL-1.4
autoreconf -i
```

### 8. Executar ./configure

```bash
./configure CPPFLAGS=-I/usr/include/postgresql LDFLAGS=-L/usr/lib/x86_64-linux-gnu
```

---

## 🛠️ Etapa 2: Compilar com make

```bash
make clean
make
sudo make install
```

---

## 🚀 Etapa 3: Testar a Instalação

### 1. Compilar um Programa de Teste

```bash
ocesql #Para validar se a biblioteca esta instalada e funcional
```
O resultado deverá ser:

Open Cobol ESQL (Ocesql)
Version 1.4.0

October 4, 2024

Tokyo System House Co., Ltd. <opencobol@tsh-world.co.jp>

```bash
cd ~/Open-COBOL-ESQL-1.4/sample
cobc -x -o test <sample_program>.cbl
./test
```

### 2. Garantir que o PostgreSQL está ativo

```bash
sudo systemctl status postgresql
sudo systemctl start postgresql
```

### 3. Criar Banco e Usuário de Teste

```bash
sudo -u postgres psql -c "CREATE DATABASE testdb;"
sudo -u postgres psql -c "CREATE USER testuser WITH PASSWORD 'testpass';"
sudo -u postgres psql -c "GRANT ALL PRIVILEGES ON DATABASE testdb TO testuser;"
```

---

## 🧩 Troubleshooting

### Erros no ./configure

Verifique o config.log:
```bash
less config.log
```

### Erros no make

Verifique as mensagens detalhadas de erro e certifique-se de que todas as dependências estão corretamente instaladas.

### Problemas com PostgreSQL 16?

Tente com a versão 13:
```bash
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt update
sudo apt install postgresql-13 postgresql-client-13 libpq-dev
```