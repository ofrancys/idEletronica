# Service Provider - Keycloak

Este repositório apresenta um exemplo de integração entre uma aplicação (Service Provider) e o Keycloak. O objetivo é demonstrar como autenticar e autorizar usuários em uma aplicação utilizando o Keycloak como provedor de identidade.

## Tecnologias Utilizadas

- **Node.js**: Ambiente de execução para JavaScript no lado do servidor.
- **Docker**: Plataforma para desenvolver, enviar e executar aplicações em containers.
- **Keycloak**: Solução de gerenciamento de identidade e acesso.
- **PostgreSQL**: Banco de dados relacional utilizado para armazenar dados de usuários e configurações do Keycloak.
- **Beekeeper**: Não obrigatório - Para demonstração do banco em container. Software gerenciador de SQL. 

## Como Rodar o Projeto

### Pré-requisitos

Certifique-se de que você tenha as seguintes ferramentas instaladas:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Passo 1: Baixe o ZIP do projeto

Local:

# https://github.com/ofrancys/idEletronica

Vá até o botão "<Code>" e baixe o arquivo ZIP.

Em seguida, navegue até o diretório do projeto e o abra no VS Code.

### Passo 2: Habilite o envio de e-mails no Keycloak

Abra o arquivo `realm-config.yaml` localizado no diretório `keycloak-config`. Navegue até o final do arquivo e substitua a configuração SMTP por uma configuração válida, ou se preferir, desabilite o envio de e-mails alterando o valor da propriedade para `verifyEmail: false` conforme o exemplo abaixo:

```json
  "smtpServer": {
    "replyToDisplayName": "",
    "starttls": "true",
    "auth": "true",
    "envelopeFrom": "",
    "ssl": "false",
    "port": "587",
    "host": "smtp.server.com",
    "replyTo": "",
    "from": "admin@user.com",
    "fromDisplayName": "Service Provider",
    "user": "**********",
    "password": "**********"
  }
```

### Passo 3: Iniciar o Projeto

Inicie o Docker Desktop.

No diretório raiz do projeto onde se encontra o arquivo `docker-compose.yml`, inicie o projeto executando o comando abaixo:

```bash
docker-compose up -d
```

### Passo 4: Acessar o Service Provider

Acesse a aplicação no navegador através do endereço `http://localhost:3001`.
Se houver algum erro pode entrar diretamente no diretório adm do Keycloak `http://localhost:8080/realms/master/protocol/openid-connect/auth?client_id=security-admin-console&redirect_uri=http%3A%2F%2Flocalhost%3A8080%2Fadmin%2Fmaster%2Fconsole%2F%23%2Fmaster%2Frealm-settings%2Femail&state=8dd63f38-58a5-497f-8f20-3bc7c21fd7ed&response_mode=query&response_type=code&scope=openid&nonce=fdd685bb-8ed0-4a57-b8ba-415a9f4a6832&code_challenge=8WLyKOPaFkF-OLIXH_RXSTOiTxI1blvwW0iUfkD6nTM&code_challenge_method=S256`

Realize o cadastro de um novo usuário e faça o login utilizando as credenciais cadastradas, se tudo ocorrer corretamente você será redirecionado para a página de informações do usuário autenticado.

## Referências

- [Keycloak Documentation](https://www.keycloak.org/documentation.html)
- [Fastify Documentation](https://www.fastify.io/docs/latest/)
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [Docker Documentation](https://docs.docker.com/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)

## Extra

A configuração do SMTP_PASS do arquivo `.env` dentro do diretório `service-provider` deve ser feita de acordo com sua conta no Google. 
É necessário gerar uma senha de 16 digitos em Senhas do App, com a url `gmail.com`, essa senha deve ser usada no SMTP_PASS.
