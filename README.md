# dslist

## Descrição

O **dslist** é uma API REST desenvolvida em Java com Spring Boot para gerenciamento de listas de jogos. O projeto foi criado como parte do Intensivão Java Spring, utilizando boas práticas de arquitetura, persistência com JPA/Hibernate e banco de dados PostgreSQL.

---

## Tecnologias Utilizadas

- **Java 21**
- **Spring Boot 3**
- **Spring Data JPA**
- **PostgreSQL** (produção/desenvolvimento)
- **H2 Database** (testes)
- **Maven** (gerenciamento de dependências)
- **Docker** (banco de dados em ambiente local)
- **PgAdmin** (administração do banco)

---

## Estrutura do Projeto

```
src/
  main/
    java/
      com.devsuperior.dslist/
        controllers/      # Controllers REST
        dto/              # Data Transfer Objects
        entities/         # Entidades JPA
        projections/      # Projeções para consultas customizadas
        repositories/     # Repositórios JPA
        services/         # Regras de negócio
    resources/
      application.properties         # Configuração global
      application-dev.properties     # Configuração de desenvolvimento
      application-prod.properties    # Configuração de produção
      application-test.properties    # Configuração de testes
      import.sql                     # Dados iniciais
```

---

## Configuração de Ambiente

### Banco de Dados

- **Desenvolvimento:** PostgreSQL rodando em Docker, porta padrão mapeada para 5433.
- **Testes:** H2 em memória.
- **Produção:** PostgreSQL, parâmetros via variáveis de ambiente.

### Perfis

- `dev` - Desenvolvimento
- `test` - Testes
- `prod` - Produção

Defina o perfil ativo em `application.properties`:
```
spring.profiles.active=dev
```

---

## Como Executar Localmente

1. **Clone o repositório**
2. **Configure o banco de dados PostgreSQL**
   - Recomenda-se usar Docker:
     ```
     docker run --name dev-postgresql -e POSTGRES_PASSWORD=1234567 -p 5433:5432 -d postgres:14-alpine
     ```
   - Crie o banco `dslist` e configure o usuário e senha conforme `application-dev.properties`.
3. **Instale as dependências**
   ```
   mvnw clean install
   ```
4. **Execute a aplicação**
   ```
   mvnw spring-boot:run
   ```
5. **Acesse a API**
   - Base URL: `http://localhost:8080`

---

## Endpoints Principais

- `GET /games` - Lista todos os jogos
- `GET /games/{id}` - Detalhes de um jogo
- `GET /lists` - Lista todas as listas de jogos
- `GET /lists/{id}/games` - Lista de jogos de uma lista específica
- `POST /lists/{id}/replacement` - Troca a ordem de jogos na lista especificada.

---

## Testes

- Os testes utilizam o banco H2 em memória.
- Para rodar os testes:
  ```
  mvnw test
  ```

---

## Importação de Dados

- O arquivo `import.sql` pode ser usado para popular o banco com dados iniciais.

---

## Segurança

- O projeto não implementa autenticação por padrão, mas pode ser facilmente integrado com Spring Security.

---

## Licença

Este projeto é apenas para fins de aprendizado.

---

## Contato

Dúvidas ou sugestões: pollykeller10@gmail.com
