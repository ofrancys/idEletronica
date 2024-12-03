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

# https://github.com/passosleo/service-provider-keycloak.git

Vá até o botão "<Code>" e baixe o arquivo ZIP.

Em seguida, navegue até o diretório do projeto:

```bash
cd service-provider-keycloak
```

### Passo 2: Habilite o envio de e-mails no Keycloak

Abra o arquivo `realm-config.yaml` localizado no diretório `keycloak-config`. Navegue até o final do arquivo e substitua a configuração SMTP por uma configuração válida, ou se preferir, desabilite o envio de e-mails alterando o valor da propriedade para `verifyEmail: false` conforme o exemplo abaixo:

```json
  "verifyEmail": true, // Altere para false para desabilitar ou configure as propriedades abaixo caso possua um servidor SMTP válido
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

No diretório raiz do projeto onde se encontra o arquivo `docker-compose.yml`, inicie o projeto executando o comando abaixo:

```bash
docker-compose up
```

### Passo 4: Acessar o Service Provider

Acesse a aplicação no navegador através do endereço `http://localhost:3001`.

Realize o cadastro de um novo usuário e faça o login utilizando as credenciais cadastradas, se tudo ocorrer corretamente você será redirecionado para a página de informações do usuário autenticado.

## Referências

- [Keycloak Documentation](https://www.keycloak.org/documentation.html)
- [Fastify Documentation](https://www.fastify.io/docs/latest/)
- [Node.js Documentation](https://nodejs.org/en/docs/)
- [Docker Documentation](https://docs.docker.com/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)

## Licença

Este projeto está licenciado sob a licença MIT - consulte o arquivo [LICENSE](LICENSE) para obter detalhes.