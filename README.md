# Primeiro Passo

Plataforma de acompanhamento físico em quatro níveis (conhecer, em casa, ao ar livre, academia) para quem ainda não teve coragem de começar a treinar.

É uma página única (`index.html`), sem build e sem servidor:

- **Site** (`#/`): apresentação, planos, combinados, formulários de contato e de parceria.
- **App do cliente** (`#/comecar`, `#/app`): questionário, treinos guiados, respiração, agenda, conversa, conquistas e pagamentos.
- **Painel da personal** (`#/personal`): alertas do dia, alunos, agenda, mensagens e ganhos.
- **Painel da empresa** (`#/admin`): visão geral, clientes, personais, financeiro, segurança, contatos e ajustes.

### O que já está pronto (ilustrativo)

- **Planos**: simulador com período (mensal, trimestral, semestral com desconto), aulas por semana, recomendação de nível e combo.
- **Pagamentos**: Pix, cartão e boleto com taxa própria de cada forma; repasse às personais com prazo configurável e chave Pix de recebimento.
- **Financeiro**: percentual de cada personal, taxas, receita líquida da empresa, margem, repasses e resultado dos últimos 6 meses.
- **Avaliações**: o aluno avalia a personal; só a empresa vê (a personal não recebe nota nem comentário).
- **Jornada em ordem**: cada etapa só libera depois da anterior (questionário, verificação de identidade, conversa gratuita única de 15 min, pagamento do nível 1 e assim por diante).
- **Exercícios**: biblioteca com demonstração animada, passo a passo e cuidados; a personal indica os exercícios de cada aluno com séries e recado.
- **Segurança**: verificação de identidade obrigatória (dados, CPF, documento, selfie, consentimento LGPD; no site de teste a aprovação é automática), checagem das personais (CREF e antecedentes), código de segurança em cada encontro presencial, check-in, botão de emergência e relato confidencial.

### Para virar produto real

- Login e banco de dados (ex.: Supabase ou Firebase).
- Gateway de pagamento com split (ex.: Asaas, Pagar.me, Mercado Pago).
- Serviço de verificação de identidade e biometria (ex.: unico, idwall, Serpro), com política de privacidade e tratamento de dado sensível conforme a LGPD.

Entre pelos painéis em `#/entrar`. É uma demonstração: não há login real e os dados ficam salvos só no navegador (localStorage). Para uso com clientes reais é preciso um servidor com autenticação, banco de dados e pagamento online.
