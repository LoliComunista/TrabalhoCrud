Telas do Sistema
1. Tela de Login (TelaLogin.java)
É a porta de entrada da aplicação.

Funções principais:

Permite a autenticação do utilizador mediante a introdução do e-mail/nome de utilizador e palavra-passe[cite: 10].

Valida as credenciais na tabela de utilizadores e redireciona para a Tela Principal em caso de sucesso[cite: 10].

Apresenta o indicador Status no canto inferior, exibindo se a ligação ao banco de dados MySQL está ativa ou off-line[cite: 10].

2. Tela Principal (TelaPrincipal.java)
Atua como o painel central de navegação (MDI Principal) do sistema.

Funções principais:

Contém a barra de menu superior (Cadastro, Opções, Ajuda)[cite: 8].

Disponibiliza os atalhos para abrir as janelas internas do sistema:

Cliente: Abre o formulário de cadastro de clientes[cite: 8].

Usuário: Abre o formulário de cadastro de operadores/utilizadores[cite: 8].

3. Tela de Cadastro de Usuários (telaUsuarios.java)
Janela dedicada ao gerenciamento dos utilizadores com permissão de acesso ao sistema.

Campos contidos: ID, Email, Nome e Senha[cite: 7].

Operações disponíveis (CRUD):

Adicionar: Regista um novo utilizador no banco de dados[cite: 7].

Editar: Atualiza os dados de um utilizador existente[cite: 7].

Visualizar: Consulta e carrega os dados armazenados[cite: 7].

Apagar: Remove o registo do utilizador selecionado[cite: 7].

4. Tela de Cadastro de Clientes (TelaCliente.java)
Formulário completo para a gestão da base de clientes.

Campos contidos: ID, Nome, Endereço, Cidade (menu suspenso), UF, Seleção de documento (CPF ou CNPJ), CPF/CNPJ, Telefone e Data de Nascimento[cite: 9].

Operações disponíveis (CRUD):

Adicionar: Regista um cliente completo na base de dados[cite: 9].

Editar: Modifica as informações de contacto ou endereço do cliente[cite: 9].

Visualizar: Pesquisa e exibe os detalhes do cliente selecionado[cite: 9].

Apagar: Remove o registo do cliente da base[cite: 9].

Tecnologias Utilizadas
Linguagem: Java (Swing UI)

IDE: NetBeans

Banco de Dados: MySQL (phpMyAdmin)
