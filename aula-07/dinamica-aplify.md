Instale o AWS Amplify CLI:

Abra o terminal e execute npm install -g @aws-amplify/cli.
Configure o acesso à AWS:

No AWS Academy Learner Lab não é possível criar usuários IAM, então **não use** `amplify configure` (ele cria um usuário IAM). Em vez disso, configure um perfil do AWS CLI com as credenciais temporárias do laboratório:

1. No Learner Lab, clique em **AWS Details > AWS CLI: Show** e copie o bloco exibido para o arquivo `~/.aws/credentials` (no Windows, `%USERPROFILE%\.aws\credentials`). Ele contém `aws_access_key_id`, `aws_secret_access_key` e `aws_session_token`.
2. No arquivo `~/.aws/config`, defina a região:

   ```ini
   [default]
   region = us-east-1
   ```

3. Ao executar `amplify init`, escolha o método de autenticação **AWS profile** e selecione o perfil `default`.

As credenciais mudam a cada sessão do laboratório: repita o passo 1 sempre que iniciar o Learner Lab.

> **Atenção:** o `amplify init` e o `amplify push` criam *roles* IAM (por exemplo, as *roles* de usuários autenticados e não autenticados do Cognito), o que pode ser bloqueado no Learner Lab. Se o comando falhar com erro de permissão (`AccessDenied` em `iam:CreateRole`), use a alternativa sem CLI: gere o *build* da aplicação (`npm run build`) e publique-o pelo console em **AWS Amplify > Create new app > Deploy without Git** (enviando o .zip da pasta `build`), ou hospede o site estático no S3 com CloudFront (dinâmica da aula 5).
Inicie seu projeto:

Navegue até a pasta do seu projeto e execute amplify init para inicializar o Amplify.
Adicione recursos:

Abra seu terminal ou prompt de comando.
Navegue até o diretório onde deseja criar o projeto.
Execute amplify init. O CLI perguntará sobre o nome do projeto, ambiente, editor de código preferido, tipo de app, framework, entre outros. Responda conforme apropriado para seu projeto.
Após a conclusão, o Amplify configurará o projeto localmente e criará os recursos necessários na nuvem.


Utilize amplify add auth para adicionar autenticação.
Use amplify add api para criar uma API GraphQL ou REST.
Para armazenamento de dados, execute amplify add storage.
Implante os recursos:

Execute amplify push para criar os recursos na nuvem.
Desenvolva sua aplicação:

Utilize as bibliotecas do Amplify em seu código para interagir com os serviços configurados.
Para mais detalhes, acesse a documentação oficial do AWS Amplify.


-----------------
criar um aplicativo React.js no AWS Amplify:

Instale o AWS Amplify CLI: Execute npm install -g @aws-amplify/cli.
Configure o acesso à AWS: no Learner Lab, use as credenciais de **AWS Details** num perfil do AWS CLI (veja acima), em vez de `amplify configure`.
Crie um novo projeto React: Use npx create-react-app my-app.
Inicialize o Amplify: Dentro da pasta do projeto, execute amplify init.
Adicione recursos: Por exemplo, para adicionar autenticação, use amplify add auth.
Faça o deploy: Execute amplify publish.