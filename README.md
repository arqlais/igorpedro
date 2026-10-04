# Primeiro Passo

Plataforma de acompanhamento físico em quatro níveis (conhecer, em casa, ao ar livre, academia) para quem ainda não teve coragem de começar a treinar.

É uma página única (`index.html`), sem build. Login e dados ficam no Firebase:

- **Site** (`#/`): apresentação, planos, combinados, formulários de contato e de parceria.
- **App do cliente** (`#/comecar`, `#/app`): questionário, treinos guiados, respiração, agenda, conversa, conquistas e pagamentos.
- **Painel da personal** (`#/personal`): alertas do dia, alunos, agenda, mensagens e ganhos.
- **Painel da empresa** (`#/admin`): visão geral, clientes, personais, financeiro, segurança, contatos e ajustes.

### O que já está pronto (ilustrativo)

- **Planos**: simulador com período (mensal, trimestral, semestral com desconto), aulas por semana, recomendação de nível e combo.
- **Pagamentos**: Pix, cartão e boleto com taxa própria de cada forma; repasse às personais com prazo configurável e chave Pix de recebimento.
- **Financeiro**: percentual de cada personal, taxas, receita líquida da empresa, margem, repasses e resultado dos últimos 6 meses.
- **Avaliações**: o aluno avalia a personal; só a empresa vê (a personal não recebe nota nem comentário).
- **Modo de teste**: a constante `TEST_MODE` (no início do script) libera todas as etapas obrigatórias para explorar, com cada uma sinalizada. Troque para `false` para clientes reais.
- **Jornada em ordem**: cada etapa só libera depois da anterior (questionário, verificação de identidade, conversa gratuita única de 15 min, pagamento do nível 1 e assim por diante).
- **Exercícios**: biblioteca com demonstração animada, passo a passo e cuidados; a personal indica os exercícios de cada aluno com séries e recado.
- **Proteção contra desvio de clientes**: termo de parceria da personal (não aliciamento por 12 meses, pagamentos só pela plataforma), termos de uso do aluno e alerta no chat para contato ou pagamento por fora, registrado para a empresa.
- **Vídeos**: cada exercício já tem a aba Vídeo; basta preencher o campo `video` do exercício com o link do arquivo.
- **Segurança**: verificação de identidade obrigatória (dados, CPF, documento, selfie, consentimento LGPD; a empresa aprova), checagem das personais (CREF e antecedentes), código de segurança em cada encontro presencial, check-in, botão de emergência e relato confidencial.

### Login e banco de dados (Firebase)

O site usa o projeto Firebase `primeiro-passo-a792c` para login com e-mail e senha e para guardar os dados no Firestore. Aluno, personal e empresa veem as mesmas informações, em qualquer aparelho. A configuração fica em `FIREBASE_CONFIG`, no início do script de `index.html`. Se a biblioteca do Firebase não carregar, o site volta ao modo demonstração (dados de exemplo salvos só no navegador).

Para ligar, no [console do Firebase](https://console.firebase.google.com/project/primeiro-passo-a792c):

1. **Authentication → Método de login**: ative **E-mail/senha**.
2. **Firestore Database → Criar banco de dados**: escolha a região `southamerica-east1` (São Paulo) e o modo de produção.
3. **Firestore Database → Regras**: apague o que estiver lá, cole o conteúdo de `firestore.rules` e clique em **Publicar**.
4. **Conta da empresa**: em **Authentication → Usuários → Adicionar usuário**, crie o e-mail e a senha da empresa e copie o **UID** que aparece na lista. Depois, em **Firestore Database → Dados → Iniciar coleção**, crie a coleção `admins` com um documento cujo ID é esse UID (pode ter um campo qualquer, como `nome`).

Como cada um entra:

- **Aluno**: cria a conta no fim do questionário (**Começar**) e depois entra em **Entrar → Aluno**.
- **Personal**: cria a conta em **Entrar → Personal → Criar conta de personal**. Fica "Aguardando análise" até a empresa aprovar em **Personais**. Novos alunos são ligados à primeira personal ativa; a empresa troca na ficha do aluno.
- **Empresa**: entra em **Entrar → Empresa** com a conta do passo 4.

Quem pode ver e mudar o quê está em `firestore.rules`: o aluno só vê os próprios dados e não aprova a própria identidade; a personal só vê os alunos dela e nunca as avaliações; contatos, relatos e alertas só a empresa lê.

Para testar sem mexer nos dados reais, rode `firebase emulators:start` nesta pasta e abra o site com `?emulador` no endereço.

### O que ainda falta para virar produto real

- **Pagamento online**: o aluno só consegue "informar" que pagou; a empresa confere e marca como pago em **Financeiro**. Falta ligar um gateway com split (ex.: Asaas, Pagar.me, Mercado Pago).
- **Verificação de identidade**: as fotos do documento e a selfie não são guardadas. A empresa aprova pelos dados enviados. Falta um serviço de verificação e biometria (ex.: unico, idwall, Serpro), com política de privacidade e tratamento de dado sensível conforme a LGPD.
- **Modo de teste**: `TEST_MODE` continua `true`, liberando as etapas obrigatórias. Troque para `false` antes de receber clientes.
