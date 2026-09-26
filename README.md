# Primeiro Passo

Plataforma de acompanhamento físico em quatro níveis (conhecer, em casa, ao ar livre, academia) para quem ainda não teve coragem de começar a treinar.

É uma página única (`index.html`), sem build e sem servidor:

- **Site** (`#/`): apresentação, planos, combinados, formulários de contato e de parceria.
- **App do cliente** (`#/comecar`, `#/app`): questionário, treinos guiados, respiração, agenda, conversa, conquistas e pagamentos.
- **Painel da personal** (`#/personal`): alertas do dia, alunos, agenda, mensagens e ganhos.
- **Painel da empresa** (`#/admin`): visão geral, clientes, personais, financeiro, contatos e preços.

Entre pelos painéis em `#/entrar`. É uma demonstração: não há login real e os dados ficam salvos só no navegador (localStorage). Para uso com clientes reais é preciso um servidor com autenticação, banco de dados e pagamento online.
