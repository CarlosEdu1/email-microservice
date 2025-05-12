Sistema de Microserviços: Usuário e E-mail
Este projeto é composto por dois microserviços desenvolvidos em Java com Spring Boot:

user-microservice: Gerencia o cadastro e autenticação de usuários.

email-microservice: Responsável pelo envio de e-mails transacionais, como confirmações de cadastro.

Arquitetura

O user-microservice expõe uma API REST para operações de usuário.

Ao registrar um novo usuário, o serviço envia uma requisição HTTP para o email-microservice, que processa e envia o e-mail correspondente.

Tecnologias Utilizadas
Java 17

Spring Boot

Maven

RESTful APIs

Comunicação entre serviços via HTTP

Execução Local
Pré-requisitos
Java 17+

Maven 3.8+

Docker (opcional, para banco de dados ou SMTP)

Passo a Passo
Clone os repositórios:

bash
Copiar
Editar
git clone https://github.com/CarlosEdu1/user-microservice.git
git clone https://github.com/CarlosEdu1/email-microservice.git
Compile e execute os serviços:

bash
Copiar
Editar
cd user-microservice
./mvnw spring-boot:run
Em outro terminal:

bash
Copiar
Editar
cd email-microservice
./mvnw spring-boot:run
Teste o fluxo de cadastro:

bash
Copiar
Editar
curl -X POST http://localhost:8080/users \
  -H "Content-Type: application/json" \
  -d '{"name": "João", "email": "joao@example.com", "password": "123456"}'
O email-microservice enviará um e-mail de confirmação para o endereço fornecido.

Estrutura dos Projetos
user-microservice
src/main/java/.../controller: Endpoints REST para operações de usuário.

src/main/java/.../service: Lógica de negócios.

src/main/java/.../client: Cliente HTTP para comunicação com o email-microservice.

email-microservice
src/main/java/.../controller: Endpoint REST para envio de e-mails.

src/main/java/.../service: Lógica para envio de e-mails via SMTP.

Comunicação entre Serviços
A comunicação entre os microserviços é realizada via HTTP. O user-microservice envia uma requisição POST para o email-microservice ao registrar um novo usuário:

java
Copiar
Editar
RestTemplate restTemplate = new RestTemplate();
HttpEntity<EmailRequest> request = new HttpEntity<>(emailRequest);
restTemplate.postForEntity("http://localhost:8081/emails/send", request, Void.class);
