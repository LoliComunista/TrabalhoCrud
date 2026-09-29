Um projeto simples e didático de **login com cadastro de usuários e clientes**, feito em **Java Swing** no **NetBeans** e conectado a um banco **MySQL** rodando no **XAMPP**.

Foi criado durante as aulas (SEG POA 2DM) para praticar a integração entre Java e banco de dados, e pode servir de ponto de partida para você montar algo maior.

---

## O que dá pra fazer com ele

- Entrar no sistema com e-mail e senha
- Cadastrar, consultar, editar e apagar **usuários**
- Cadastrar, consultar, alterar e apagar **clientes**
- Navegar por uma tela principal com menu (Cadastro, Opções e Ajuda)
- Ver a tela "Sobre" com os créditos do projeto

As consultas usam `PreparedStatement`, então o código já nasce protegido contra SQL Injection. E o usuário recebe uma mensagem na tela sempre que algo dá certo (ou errado).

## Feito com

- Java 8 ou superior (Swing)
- NetBeans IDE (com Apache Ant)
- MySQL via XAMPP
- MySQL Connector/J (o driver JDBC)

## Como o projeto está organizado

```
LoginUsuario2/
├── build.xml
├── manifest.mf
├── nbproject/                 # configurações do NetBeans
└── src/
    ├── dal/
    │   └── Mod_conexao.java   # conexão com o banco
    ├── icones/                # ícones da interface
    └── telas/
        ├── TelaLogin.java     # tela inicial (classe principal)
        ├── TelaPrincipal.java # menu do sistema
        ├── TelaCliente.java   # CRUD de clientes
        ├── telaUsuarios.java  # CRUD de usuários
        └── TelaSobre.java     # créditos
```

## Antes de começar

Você vai precisar ter instalado:

- [JDK 8+](https://adoptium.net/)
- [NetBeans](https://netbeans.apache.org/)
- [XAMPP](https://www.apachefriends.org/) com o MySQL
- O [MySQL Connector/J](https://dev.mysql.com/downloads/connector/j/) (arquivo `.jar`)

## Preparando o banco de dados

1. Abra o XAMPP e inicie o **MySQL**.
2. Entre no phpMyAdmin: `http://localhost/phpmyadmin`.
3. Na aba **SQL**, cole e execute isto:

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

-- Usuário para o primeiro acesso
INSERT INTO tb_usuarios (nome, email, senha)
VALUES ('Administrador', 'admin@admin.com', 'admin');
```

Os nomes das tabelas e colunas seguem exatamente o que o código espera. Já os tipos de dados são só uma sugestão, ajuste como preferir.

### Conexão

Os dados de conexão ficam em `src/dal/Mod_conexao.java`:

```java
String url      = "jdbc:mysql://localhost:3306/bancoJava";
String user     = "root";
String password = "";   // padrão do XAMPP
```

Se o seu MySQL usa outra porta, usuário ou senha, é só mudar aí.

## Rodando o projeto

1. Clone o repositório:
   ```bash
   git clone https://github.com/<seu-usuario>/<seu-repositorio>.git
   ```
2. Abra a pasta no NetBeans (`File > Open Project`).
3. Adicione o driver: clique com o botão direito em **Libraries > Add JAR/Folder** e escolha o `mysql-connector-j-x.x.x.jar`.
   *Dica: se o NetBeans reclamar de uma referência quebrada, é porque o projeto guardou o caminho do JAR no computador de quem criou. Remova a referência e adicione o arquivo de novo.*
4. Confira se o MySQL do XAMPP está rodando e se o banco `bancoJava` existe.
5. Aperte **F6** para executar (a classe principal é `telas.TelaLogin`).
6. Entre com `admin@admin.com` e `admin`, se você usou o script acima.

## Por onde o usuário passa

```
TelaLogin ──► TelaPrincipal
                ├── Cadastro > Cliente  ──► TelaCliente
                ├── Cadastro > Usuário  ──► telaUsuarios
                ├── Ajuda    > Sobre    ──► TelaSobre
                └── Opções   > Sair     ──► fecha o programa
```

## Ainda dá pra melhorar

Como é um projeto de estudo, algumas coisas ficaram simples de propósito. Se você quiser levar isso mais a sério, vale começar por aqui:

- **Senhas em texto puro:** hoje elas são salvas e comparadas exatamente como digitadas. O ideal é guardar um hash com salt (o **BCrypt** é uma boa opção).
- **`getText()` no campo de senha:** está obsoleto, o recomendado é `getPassword()`.
- **Conexão como `root` sem senha:** funciona bem para testar, mas o certo é criar um usuário do MySQL só para o sistema e tirar as credenciais de dentro do código.
- **Sem níveis de acesso:** todo mundo que entra pode fazer tudo.

E para evoluir: recuperação de senha, perfis (admin e usuário comum), validação de CPF e datas, listagem em tabela (`JTable`) e testes automatizados.

## Quem fez

Criado por **Flavio Silva** em 22/02/2024, com revisão do **João Pedro**.

Ficou com dúvida, achou um bug ou tem uma ideia? Abra uma *issue* ou mande um *pull request*. Contribuições são bem-vindas! 🙂

<!-- Se quiser definir os termos de uso, adicione aqui uma licença (por exemplo, MIT). -->
