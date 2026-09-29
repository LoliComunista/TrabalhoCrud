Sistema de Gestão e Login (LoginUsuarioARG)Este projeto é uma aplicação desktop desenvolvida em Java (Swing UI) no ambiente NetBeans IDE, integrada com banco de dados MySQL via XAMPP. O sistema oferece autenticação de acessos e gerenciamento completo de cadastros (CRUD) para utilizadores e clientes.   Estrutura das Telas do Sistema1. Tela de Login (TelaLogin.java)Ponto de entrada do sistema[cite: 10, 12].Funções principais:Autenticação de utilizadores com verificação de credenciais no banco de dados[cite: 10, 14].Indicador visual de Status da conexão MySQL via módulo Mod_conexao (ícone verde para conexão ativa, ícone vermelho para offline)[cite: 10, 12].2. Tela Principal (TelaPrincipal.java)Janela MDI principal que serve como painel central da aplicação[cite: 8, 12].Funções principais:Barra de navegação com menus de Cadastro, Opções e Ajuda[cite: 8].Atalhos diretos para abertura dos formulários internos de Cliente e Usuário[cite: 8].3. Tela de Cadastro de Usuários (telaUsuarios.java)Gerenciamento das contas de operadores com acesso ao sistema[cite: 7, 12].Campos do formulário: ID, Email, Nome e Senha[cite: 7].Operações disponíveis (CRUD):Adicionar: Cadastra novos utilizadores[cite: 7].Editar: Atualiza os dados de cadastros existentes[cite: 7].Visualizar: Realiza a consulta e carregamento dos registos[cite: 7].Apagar: Remove o utilizador selecionado[cite: 7].4. Tela de Cadastro de Clientes (TelaCliente.java)Formulário para controle e manutenção da base de clientes[cite: 9, 12].Campos do formulário: ID, Nome, Endereço, Cidade, UF, Tipo de Documento (CPF/CNPJ), Número do Documento, Telefone e Data de Nascimento[cite: 9].Operações disponíveis (CRUD):Adicionar: Regista um novo cliente no banco de dados[cite: 9].Editar: Altera informações cadastrais e de contato[cite: 9].Visualizar: Localiza e exibe os dados do cliente[cite: 9].Apagar: Exclui o registo do cliente[cite: 9].5. Tela Sobre (TelaSobre.java)Janela informativa referente aos créditos, versão e detalhes de desenvolvimento do projeto[cite: 12].LoginUsuarioARG/
├── build.xml
├── README.md
└── src/
    ├── dal/
    │   └── Mod_conexao.java       # Módulo de conexão com banco MySQL
    ├── icones/
    │   ├── KnobCancel.png         # Ícone de status offline
    │   └── KnobValidGreen.png     # Ícone de status online
    └── telas/
        ├── TelaCliente.java       # Form de cadastro de clientes
        ├── TelaLogin.java         # Form de autenticação de acesso
        ├── TelaPrincipal.java     # Janela MDI principal
        ├── TelaSobre.java         # Informações do sistema
        └── telaUsuarios.java      # Form de cadastro de utilizadores
```[cite: 11, 12, 14]

---

## Tecnologias Utilizadas

* **Linguagem:** Java (Swing UI)[cite: 14]
* **IDE:** NetBeans IDE[cite: 11, 14]
* **Automação de Build:** Apache Ant (`build.xml`)[cite: 11]
* **Banco de Dados:** MySQL (XAMPP / phpMyAdmin)[cite: 14]
