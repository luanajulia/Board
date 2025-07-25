# 📋 Gerenciador de Boards em Java

Este projeto é uma aplicação de linha de comando (CLI) desenvolvida em Java com Gradle, que permite gerenciar boards (quadros Kanban simplificados). Ele suporta operações CRUD básicas para boards e suas colunas (como 'To Do', 'Doing', 'Done'), além de funcionalidades de gerenciamento de cards, incluindo bloqueio e movimentação entre colunas.

O projeto utiliza **MySQL** como banco de dados e **Liquibase** para gerenciamento de migrações de esquema, garantindo que o banco de dados esteja sempre na versão correta.

## 🚀 Funcionalidades

* **Gerenciamento de Boards:**
    * Criar novas boards.
    * Listar todas as boards existentes.
    * Selecionar uma board para gerenciar seus cards e colunas.
    * Excluir boards.
* **Gerenciamento de Colunas (padrão):**
    * Boards são criadas com colunas padrão (e.g., INITIAL, FINAL, CANCEL, PENDING).
    * Visualização de colunas e seus respectivos cards.
* **Gerenciamento de Cards:**
    * Criar cards em uma board específica.
    * Mover cards entre as colunas.
    * Bloquear e desbloquear cards com motivos.
    * Cancelar cards.
    * Visualizar detalhes de um card (título, descrição, status de bloqueio, histórico de bloqueios).

## 🛠️ Tecnologias Utilizadas

* **Java 17+**: Linguagem de programação.
* **Gradle**: Ferramenta de automação de build.
* **MySQL**: Sistema de gerenciamento de banco de dados relacional.
* **Liquibase**: Ferramenta para controle de versão de banco de dados.
* **Lombok**: Biblioteca para reduzir boilerplate code.
* **JUnit 5 (Opcional, se houver testes)**: Framework de testes unitários.

## ⚙️ Pré-requisitos

Antes de começar, certifique-se de ter as seguintes ferramentas instaladas:

* **JDK (Java Development Kit)**: Versão 17 ou superior.
    * [Baixar OpenJDK](https://openjdk.java.net/install/index.html)
* **MySQL Server**: Versão 8.0 ou superior.
    * [Baixar MySQL Community Server](https://dev.mysql.com/downloads/mysql/)
* **Gradle**: (Opcional, o projeto já inclui o Gradle Wrapper `gradlew`)
    * [Instalar Gradle](https://gradle.org/install/)
* **Git**: Para clonar o repositório.
    * [Baixar Git](https://git-scm.com/downloads)

## 📦 Configuração do Banco de Dados

1.  **Crie o banco de dados MySQL:**
    ```sql
    CREATE DATABASE board;
    ```

2.  **Crie um usuário e conceda permissões:**
    ```sql
    CREATE USER 'board'@'localhost' IDENTIFIED BY 'board';
    GRANT ALL PRIVILEGES ON board.* TO 'board'@'localhost';
    FLUSH PRIVILEGES;
    ```
    * **Importante**: Certifique-se de que o usuário `board` possa acessar o banco de dados `board` com a senha `board`. Se usar credenciais diferentes, você precisará atualizar o arquivo `ConnectionConfig.java`.

3.  **Verifique a conexão (opcional):**
    Você pode tentar conectar-se via terminal para garantir que o usuário e a senha estão corretos:
    ```bash
    mysql -u board -p
    # Digite 'board' quando solicitado pela senha
    USE board;
    EXIT;
    ```

## 🚀 Como Executar o Projeto

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/luanajulia/Board.git](https://github.com/luanajulia/Board.git)
    cd Board
    ```

2.  **Abra o projeto no IntelliJ IDEA (ou sua IDE preferida):**
    * No IntelliJ, vá em `File` > `Open...` e selecione a pasta `Board` que você clonou.
    * Deixe o IntelliJ sincronizar o projeto Gradle e baixar as dependências.
    * **Configure o Lombok no IntelliJ:** Vá em `File` > `Settings` > `Build, Execution, Deployment` > `Compiler` > `Annotation Processors` e marque `Enable annotation processing`. Clique em OK.

3.  **Execute as Migrações do Liquibase:**
    As migrações do banco de dados serão executadas automaticamente na primeira vez que você rodar a aplicação através do método `main` da classe `Main`.
    Você pode verificar o log `liquibase.log` na raiz do projeto para ver o resultado das migrações.

4.  **Execute a Aplicação:**
    * A partir do IntelliJ IDEA, localize a classe `Main.java` (geralmente em `src/main/java/br/com/dio/Main.java`).
    * Clique com o botão direito na classe `Main` e selecione `Run 'Main.main()'`.
    * A aplicação será iniciada no console (terminal) do IntelliJ.

    Ou via linha de comando:
    ```bash
    ./gradlew run
    ```

## 🤝 Contribuição

Contribuições são bem-vindas! Se você deseja contribuir, siga estes passos:

1.  Faça um fork do repositório.
2.  Crie uma nova branch (`git checkout -b feature/sua-feature`).
3.  Faça suas alterações e comite-as (`git commit -m 'feat: Adiciona nova funcionalidade'`).
4.  Envie suas alterações para a sua branch no fork (`git push origin feature/sua-feature`).
5.  Abra um Pull Request para a branch `main` deste repositório.

## 📄 Licença

Este projeto está licenciado sob a licença [MIT License](LICENSE).

---

### Personalização:

* **`[Seu Nome ou Nome da Organização]`**: Adicione seu nome ou o nome da sua organização na seção de Licença.
* **`[Link para o License]`**: Crie um arquivo `LICENSE` na raiz do seu projeto e adicione o conteúdo da licença MIT nele. O GitHub geralmente permite adicionar isso automaticamente ao criar o repositório.
* **`[Seu Usuário do GitHub]`**: No link de `git clone`, substitua `luanajulia` pelo seu nome de usuário.
* **Capturas de Tela (Opcional)**: Se for uma aplicação gráfica, adicionar screenshots da interface pode ser muito útil. Para CLI, menos comum, mas você pode mostrar exemplos de interação no terminal.
* **Testes (Se houver)**: Se você tiver testes, adicione uma seção "Como Rodar os Testes" com o comando `./gradlew test`.

Este `README.md` oferece uma visão geral completa do seu projeto, facilitando para outras pessoas (e para você mesmo no futuro) entenderem e usarem o código.
