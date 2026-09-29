# Sistema de Login e CRUD em Java + MySQL (XAMPP)

Aplicação desktop em **Java Swing** desenvolvida no **NetBeans IDE**, com autenticação de usuários e cadastro (CRUD) de **usuários** e **clientes**, integrada a um banco de dados **MySQL** rodando no **XAMPP**.

> Projeto educacional (SEG POA 2DM). Serve como base para sistemas de login mais completos em Java.

---

## Sumário

- [Funcionalidades](#funcionalidades)
- [Tecnologias](#tecnologias)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Pré-requisitos](#pré-requisitos)
- [Configuração do banco de dados](#configuração-do-banco-de-dados)
- [Como executar](#como-executar)
- [Fluxo da aplicação](#fluxo-da-aplicação)


---

## Funcionalidades

- **Login** com e-mail e senha, validados contra a tabela `tb_usuarios`.
- **Tela principal** com menu: Cadastro (Cliente / Usuário), Opções (Sair) e Ajuda (Sobre).
- **CRUD de usuários**: adicionar, visualizar (consulta por ID), editar e apagar.
- **CRUD de clientes**: adicionar, consultar (por ID), alterar e apagar.
- **Tela "Sobre"** com informações do sistema.
- Consultas SQL com `PreparedStatement` (protege contra SQL Injection).
- Mensagens de feedback ao usuário via `JOptionPane`.

## Tecnologias

| Tecnologia | Uso |
|---|---|
| Java 8+ (Swing) | Linguagem e interface gráfica |
| NetBeans IDE | Ambiente de desenvolvimento e Form Designer (`.form`) |
| Apache Ant | Build do projeto (`build.xml`) |
| MySQL (via XAMPP) | Banco de dados |
| MySQL Connector/J | Driver JDBC (`com.mysql.cj.jdbc.Driver`) |

## Estrutura do projeto

```
LoginUsuario2/
├── build.xml                  # Script de build do Ant (gerado pelo NetBeans)
├── manifest.mf
├── nbproject/                 # Configurações do projeto NetBeans
└── src/
    ├── dal/
    │   └── Mod_conexao.java   # Conexão com o banco (JDBC)
    ├── icones/                # Ícones usados na interface
    └── telas/
        ├── TelaLogin.java     # Tela de login (classe principal)
        ├── TelaPrincipal.java # Tela principal com menu
        ├── TelaCliente.java   # CRUD de clientes
        ├── telaUsuarios.java  # CRUD de usuários
        └── TelaSobre.java     # Informações do sistema
```

## Pré-requisitos

- [JDK 8 ou superior](https://adoptium.net/)
- [NetBeans IDE](https://netbeans.apache.org/)
- [XAMPP](https://www.apachefriends.org/) (com o módulo MySQL)
- [MySQL Connector/J](https://dev.mysql.com/downloads/connector/j/) (arquivo `.jar`)

## Configuração do banco de dados

1. Abra o **XAMPP Control Panel** e inicie o **MySQL**.
2. Acesse o **phpMyAdmin** em `http://localhost/phpmyadmin`.
3. Execute o script abaixo na aba **SQL**:

```sql
CREATE DATABASE IF NOT EXISTS bancoJava
  CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
USE bancoJava;

CREATE TABLE tb_usuarios (
  id    INT AUTO_INCREMENT PRIMARY KEY,
  nome  VARCHAR(100) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  senha VARCHAR(100) NOT NULL
);

CREATE TABLE tb_clientes (
  id_cliente        INT AUTO_INCREMENT PRIMARY KEY,
  nome_cliente      VARCHAR(100) NOT NULL,
  endereco_cliente  VARCHAR(150),
  cidade_cliente    VARCHAR(80),
  uf_cliente        CHAR(2),
  cpf_cliente       VARCHAR(14),
  telefone_cliente  VARCHAR(20),
  dat_nasc_cliente  VARCHAR(10)
);

-- Usuário inicial para o primeiro acesso
INSERT INTO tb_usuarios (nome, email, senha)
VALUES ('Administrador', 'admin@admin.com', 'admin');
```

> Os nomes das tabelas e colunas acima correspondem às consultas SQL usadas no código. Os tipos de dados são uma sugestão e podem ser ajustados.

### Parâmetros de conexão

Definidos em `src/dal/Mod_conexao.java`:

```java
String url      = "jdbc:mysql://localhost:3306/bancoJava";
String user     = "root";
String password = "";   // padrão do XAMPP
```



## Fluxo da aplicação

```
TelaLogin ──(credenciais válidas)──► TelaPrincipal
                                       ├── Cadastro > Cliente  ──► TelaCliente
                                       ├── Cadastro > Usuário  ──► telaUsuarios
                                       ├── Ajuda    > Sobre    ──► TelaSobre
                                       └── Opções   > Sair     ──► encerra a aplicação
`
