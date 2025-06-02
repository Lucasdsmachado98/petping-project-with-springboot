# PETPING - Backend (Java Spring Boot)

Este repositório contém o código-fonte da API backend do projeto PETPING, desenvolvida em Java com Spring Boot.

## Sobre o Projeto

PETPING é um sistema de rastreamento de animais de estimação. Este backend atua como a API central do sistema, responsável por:

*   Gerenciar dados de Tutores e Pets.
*   Processar a lógica de negócio.
*   Receber ou buscar dados de localização do Firebase (ou diretamente da coleira, dependendo da arquitetura final).
*   Fornecer endpoints RESTful para as interfaces frontend (Web React e Aplicativo Mobile).
*   Gerenciar autenticação e autorização de usuários (Tutores).

## Tecnologias Utilizadas

*   **Java:** (Versão JDK - ex: 17 ou 21)
*   **Spring Boot:** Framework principal para desenvolvimento da aplicação.
*   **Spring Web:** Para criação de APIs RESTful.
*   **Spring Data JPA:** Para persistência de dados em banco relacional (se aplicável).
*   **[Banco de Dados - ex: PostgreSQL, MySQL, H2]:** Para armazenamento dos dados de Tutores e Pets.
*   **Firebase Admin SDK:** Para interação com o Firebase (ex: leitura de dados de localização, autenticação).
*   **[Gerenciador de Dependências - Maven ou Gradle]:** Para gerenciamento do projeto e suas bibliotecas.
*   **Spring Security:** (Opcional, mas recomendado) Para controle de acesso e segurança.
*   **Lombok:** (Opcional) Para reduzir código boilerplate.

## Pré-requisitos

Antes de começar, certifique-se de ter instalado em sua máquina:

*   **JDK (Java Development Kit):** (Versão compatível com o projeto, ex: 17+)
*   **Maven** ou **Gradle:** (Dependendo do gerenciador escolhido para o projeto)
*   **[Cliente do Banco de Dados]:** (Ex: DBeaver, pgAdmin, MySQL Workbench) - Opcional, para visualização.
*   **[Instância do Banco de Dados]:** (Rodando localmente ou acessível remotamente, se não usar H2 em memória).
*   **IDE Java:** (Ex: IntelliJ IDEA, Eclipse, VS Code com extensões Java).

## Configuração do Ambiente

1.  **Clone o repositório:**
    ```bash
    git clone [URL_DO_REPOSITORIO_BACKEND]
    cd [NOME_DA_PASTA_DO_PROJETO_BACKEND]
    ```

2.  **Configure as propriedades da aplicação:**
    *   Localize o arquivo `src/main/resources/application.properties` (ou `application.yml`).
    *   Configure a conexão com o banco de dados (URL, usuário, senha):
        ```properties
        # Exemplo para PostgreSQL
        spring.datasource.url=jdbc:postgresql://localhost:5432/petping_db
        spring.datasource.username=seu_usuario
        spring.datasource.password=sua_senha
        spring.jpa.hibernate.ddl-auto=update # ou validate, create-drop
        spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
        ```
    *   Configure as credenciais do Firebase:
        *   Obtenha o arquivo JSON de credenciais da sua conta de serviço no Firebase Console.
        *   Configure o caminho para este arquivo nas propriedades ou via variável de ambiente (método recomendado para segurança).
        ```properties
        # Exemplo (não ideal para produção - melhor usar variável de ambiente)
        # firebase.service-account.file=path/to/your/serviceAccountKey.json
        ```
        *   Consulte a documentação do Firebase Admin SDK para a inicialização correta no Spring Boot.

3.  **Instale as dependências (Maven/Gradle):**
    *   A IDE geralmente faz isso automaticamente ao importar o projeto.
    *   Se necessário, via linha de comando:
        *   Maven: `mvn clean install`
        *   Gradle: `gradle build`

## Rodando o Projeto Localmente

Após a configuração, você pode iniciar a aplicação Spring Boot:

*   **Pela IDE:** Procure pela classe principal (com a anotação `@SpringBootApplication`) e execute-a como "Java Application".
*   **Via linha de comando:**
    *   Maven: `mvn spring-boot:run`
    *   Gradle: `gradle bootRun`

A API estará disponível, por padrão, em `http://localhost:8080`.

## Endpoints da API

Os endpoints disponíveis podem ser consultados através de:

*   **Swagger UI:** Se configurado, geralmente acessível em `http://localhost:8080/swagger-ui.html`.
*   **[Link para Documentação da API]:** (Se houver documentação separada, ex: Postman Collection, Wiki).

Principais endpoints esperados:

*   `/api/auth/register` (POST): Cadastro de Tutor.
*   `/api/auth/login` (POST): Login de Tutor.
*   `/api/tutors/me` (GET/PUT): Gerenciamento do perfil do Tutor logado.
*   `/api/pets` (POST/GET): Cadastro e listagem de Pets do Tutor logado.
*   `/api/pets/{petId}` (GET/PUT/DELETE): Gerenciamento de um Pet específico.
*   `/api/pets/{petId}/location` (GET): Obtenção da última localização de um Pet.
*   `/api/pets/locations` (GET): Obtenção das localizações de todos os Pets do Tutor.

## Build da Aplicação

Para gerar o artefato executável (JAR ou WAR):

*   Maven: `mvn clean package`
*   Gradle: `gradle build`

O arquivo gerado estará na pasta `target` (Maven) ou `build/libs` (Gradle).

## Contribuição

[Instruções sobre como contribuir, se aplicável - ex: padrões de código, fluxo de branches, etc.]

## Licença

[Tipo de Licença - ex: MIT]

