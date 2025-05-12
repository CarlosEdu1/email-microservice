# Sistema de Microserviços: Usuário e E-mail

Este projeto é composto por dois microserviços desenvolvidos em Java com Spring Boot:

- **[user-microservice](https://github.com/CarlosEdu1/user-microservice)**: Gerencia o cadastro e autenticação de usuários.
- **[email-microservice](https://github.com/CarlosEdu1/email-microservice)**: Responsável pelo envio de e-mails transacionais, como confirmações de cadastro.

## Arquitetura

1. O `user-microservice` expõe uma API REST para operações de usuário.
2. Ao registrar um novo usuário, o serviço envia uma requisição HTTP para o `email-microservice`, que processa e envia o e-mail correspondente.

## Tecnologias Utilizadas

- Java 17
- Spring Boot
- Maven
- RESTful APIs
- Comunicação entre serviços via HTTP

## Execução Local

### Pré-requisitos

- Java 17+
- Maven 3.8+
- Docker (opcional, para banco de dados ou SMTP)

### Passo a Passo

1. Clone os repositórios:

   ```bash
   git clone https://github.com/CarlosEdu1/user-microservice.git
   git clone https://github.com/CarlosEdu1/email-microservice.git
