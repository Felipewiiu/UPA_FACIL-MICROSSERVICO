<div align="center">
<a href="https://www.fiap.com.br" target="_blank">
    <img src="https://on.fiap.com.br/theme/fiap/postech/pos-tech.png" height="100px" alt="FIAP" class="center"/>
</a>

[![Java11](https://img.shields.io/badge/devel-Java-brightgreen)](https://docs.oracle.com/en/java/javase/11)
[![SpringBoot](https://img.shields.io/badge/framework-SpringBoot-brightgreen)](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle)
[![Docker](https://img.shields.io/badge/container-Docker-brightgreen)](https://www.docker.com)
</div>


# TRABALHO DE CONCLUSÃO - FASE 5

# 📌 UPA FÁCIL

## 🎯 Problema identificado

Em casos de grandes emergências, os pacientes podem enfrentar dificuldades para encontrar a unidade mais próxima ou com
menor tempo de espera, resultando em superlotação de algumas unidades enquanto outras permanecem subutilizadas.
Observamos que, além disso, a falta de informações em tempo real sobre a fila de atendimento pode causar frustração para
os pacientes e dificultar a gestão dos recursos de saúde.

## 📝 Descrição da solução

A API **ms-filtro-unidade-atendimento** tem como principal objetivo facilitar o direcionamento de pacientes para a
Unidade de Pronto Atendimento (UPA) mais próxima e com menor tempo de espera. Com essa API, é possível acompanhar em
tempo real a fila de atendimento das UPAs, registrar e liberar atendimentos, além de consultar as unidades disponíveis.

## 🚀 Funcionalidades

- 🔍 **Localizar a UPA mais próxima do paciente**
- 📉 **Identificar a UPA com menor fila de atendimento**
- 🏥 **Gerenciar UPAs (Cadastro, Atualização e Remoção)**
- ⏳ **Monitorar o fluxo de atendimento em tempo real**

## 🔗 Endpoints Principais

### 📊 Monitoramento e Fila de Atendimento

- `GET /upa/real-time-queue` → Acompanha a fila de atendimento em tempo real
- `GET /upa/lower-queue/state/{state}` → Retorna a UPA com menor fila de atendimento
- `GET /upa/near-upa` → Retorna a UPA mais próxima do paciente segundo a sua localização
- `GET /upa/register-service/{upaId}` → Adiciona paciente na fila de atendimento
- `GET /upa/frees-queue/{upaId}` → Retira paciente da fila de atendimento

### 📌 Gestão de UPAs

- `POST /upa/create` → Cadastra uma nova UPA
- `GET /upa/{id}` → Busca uma UPA pelo ID
- `GET /upa/all` → Retorna todas as UPAs disponíveis
- `PATCH /upa/update/{id}` → Atualiza informações da UPA
- `DELETE /upa/delete/{id}` → Remove uma UPA do sistema

## 📦 Tecnologias Utilizadas

- Java com Spring Boot
- Banco de Dados PostgreSQL
- MapStruct para mapeamento de entidades
- Clean Architecture
- Webflux
- SSE - server sent events
- Docker
- flyway para controle de migrações
- Swagger
- Spring cloud netflix
- Algoritimo de haversine para cálculo de distâncias

## 🛠 Como Executar localmente

1. Clone este repositório:
   ```bash
   git clone --recurse-submodules https://github.com/Felipewiiu/UPA_FACIL-MICROSSERVICO.git
   ```
2. Configure as variáveis de ambiente no arquivo `.env` ou `application.properties`.
3. Execute a aplicação com o Maven:
   ```bash
   mvn spring-boot:run
   ```
4. Acesse a documentação da API via Swagger:
   ```
   http://localhost:<PORTA>/swagger-ui/webjars/swagger-ui/index.html
   ```

## 🛠 Como Executar via Docker

1. Entre na raíz de cada microserviço e crie a imagem deles com os seguintes comandos

````shell
docker build -t ms-api-gateway:1.0 .
````

````shell
docker build -t ms-server-eureka:1.0 .
````

````shell
docker build -t ms-filtro-unidade-atendimento:1.0 .
````

2. Depois das imagens criadas execute o seguinte comando na raíz do projeto:

````shell
docker-compose up
````

## 🐾 PRÓXIMOS PASSOS

- Como proximos passos, implementaremos o restante do ecosistemas de de microsserviços como:

#### MS-AGENDAMENTO DE CONSULTAS

- Microsserviço onde o cliente poderá se cadastrar, agendar e ver as disponibilidades de horários e serviços oferecidos
  nas unidades UBS.

#### SISTEMA DE AUTENTICAÇÃO E AUTORIZAÇÃO

-   Adição Token JWT ou auth 0 para segurança dos dados.

#### MS-OPEN SAÚDE

- Microsserviço responsável por fornecer prontuários eletrônicos unificados para hospitais públicos e privados acessarem
  os dados dos pacientes cadastrados, (OPEN SAÚDE), todos os hospitais públicos e privados poderão ver a ficha de
  pacientes quando cadastrados.

#### MS-GESTÃO INSUMOS

- Microsserviço responsável pela gestão de estoque mínimo de insumos para controle de todo o material hospitalar
  prevenindo desfalque de materiais.

#### MS-TELE MEDICINA

- Microsserviço responsável pelo Teleatendimento virtual com chamadas de vídeos, onde o paciente poderá obter
  atendimento prévio sem precisar sair de casa

#### MS-GESTÃO DE ATENDIMENTO

- Microsserviço responsável pela gerencia do atendimento ao pacientes, nele podemos consumir os dados da fila do filtro
  de atendimento para prestar consulta e finalizar o atendimento.

#### MS-NOTIFICAÇÃO AO PACIENTE

- Microsserviço de envio de mensagens para pacientes em espera de atendimento

## ARQUITETURA DE SISTEMAS

![img.png](img.png)
----
## 📝 Licença

Este projeto está sob a licença MIT.

