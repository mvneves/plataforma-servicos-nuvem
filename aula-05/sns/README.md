# Publicar mensagens no SNS pelo SDK e pelo AWS CLI

## Pré-requisitos

- **AWS CLI v2:** siga o guia oficial de instalação para o seu sistema operacional (Windows, macOS ou Linux):
  [docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).
- **Credenciais:** no AWS Academy Learner Lab, copie o bloco de **AWS Details > AWS CLI: Show** para o arquivo
  `~/.aws/credentials` (ele inclui o `aws_session_token`, que muda a cada sessão).
- **Node.js** para executar o `send.js`.

## Executar

1. Troque a região e o `TopicArn` em `send.js` pelos do tópico que você criou na dinâmica (o ARN aparece na página
   do tópico no console do SNS).
2. Instale as dependências e execute:

   ```bash
   npm install
   node send.js
   ```

Pelo AWS CLI:

```bash
aws sns publish --topic-arn "<ARN do seu tópico>" --message "Test message" --region us-east-1
```
