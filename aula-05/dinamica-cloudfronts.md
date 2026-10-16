# Dinamica CloudFront
## Passo 1: Preparar o Website Estático
* **Criar o Conteúdo do Website**: Desenvolva seu website estático. Para esta dinâmica, você pode criar um simples arquivo HTML chamado index.html. Exemplo de conteúdo:
html

```htm
<!DOCTYPE html>
<html>
<head>
    <title>Meu Website na CloudFront</title>
</head>
<body>
    <h1>Bem-vindo ao Meu Website Hospedado via AWS CloudFront!</h1>
    <p>Este é um teste de conteúdo distribuído globalmente.</p>
</body>
</html>
```
## Passo 2: Configurar o Amazon S3
* **Criar** um Bucket no S3: Acesse o console da AWS, vá até o serviço S3 e crie um novo bucket. **Desmarque** a opção "Bloquear todo o acesso público" e **aceite** as configurações padrão. Edite a Política do Bucket e adicione  as pólieces, Lembre-se de dar um nome único ao seu bucket.

* **Upload** do Conteúdo: Faça o upload do seu arquivo index.html para o bucket.

* **Configurar** o Bucket para Hospedagem de Website: Na aba "Propriedades" do bucket, ative a opção "Hospedagem de site estático", defina o index.html como documento de índice.

## Passo 3: Criar uma Distribuição CloudFront
* **Acessar o CloudFron**t: No console da AWS, vá até o serviço CloudFront e clique em "Criar distribuição".
* **Configurar** a Origem: Escolha seu bucket S3 como origem. Use o endpoint do bucket que não inclui o nome do bucket no domínio (por exemplo, s3-website-us-east-1.amazonaws.com).
* Configurações Adicionais: **Mantenha** as configurações padrão, mas preste atenção à política de cache e à distribuição de TLS/SSL conforme necessário.
Lançar a Distribuição: Após configurar, clique em "Criar distribuição". O processo pode levar alguns minutos.

## Passo 4: Testar o Acesso ao Website
* **Obter** o Domínio CloudFront: Após a distribuição estar ativa, copie o domínio fornecido pelo CloudFront (por exemplo, d1234.cloudfront.net).
* **Acessar** o Website: Cole o domínio em seu navegador. Você deverá ver seu website sendo servido através do CloudFront, com o conteúdo entregue pelo ponto de presença (PoP) mais próximo.

## Para saber mais: bucket privado com Origin Access Control (OAC)

Nesta dinâmica o bucket fica público, o que funciona, mas é o padrão antigo: qualquer pessoa pode acessar os arquivos direto pelo S3, sem passar pelo CloudFront. A prática recomendada atualmente é manter o bucket **privado** (com "Bloquear todo o acesso público" ligado e sem hospedagem de site estático) e liberar o acesso só para o CloudFront, com *Origin Access Control*:

* Ao criar a distribuição, escolha como origem o endpoint REST do bucket (`<bucket>.s3.<região>.amazonaws.com`), e não o endpoint de site estático.
* Em **Origin access**, selecione **Origin access control settings (recommended)** e crie um OAC.
* Defina `index.html` como **Default root object** da distribuição.
* Depois de criar a distribuição, copie a política de bucket sugerida pelo CloudFront e cole-a na aba **Permissões** do bucket.

Mais detalhes na [documentação do CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html).
