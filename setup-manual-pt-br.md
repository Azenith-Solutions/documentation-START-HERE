# Hardware Tech - Manual de Instalação

Bem-vindo ao guia de instalação do projeto Hardware Tech. Este documento fornece instruções passo a passo para configurar o ambiente necessário e colocar o projeto em funcionamento no seu sistema.

Este manual tem como foco exclusivo o processo de instalação. Para uma documentação mais abrangente sobre as funcionalidades do projeto, arquitetura, API e padrões de uso, consulte nossa [documentação](https://github.com/Azenith-Solutions/documentation-START-HERE) [principal](https://github.com/Azenith-Solutions/documentation-START-HERE).

## Sumário

*   [Pré-requisitos](#pré-requisitos)
*   [Obtenção do Código](#obtenção-do-código)
*   [Instalação](#instalação)
*   [Configuração](#configuração)
    *   [Configuração de Ambiente](#configuração-de-ambiente)
    *   [Configuração do Banco de Dados](#configuração-do-banco-de-dados)
    *   [Configuração de Serviços Externos](#configuração-de-serviços-externos)
*   [Execução do Projeto](#execução-do-projeto)
*   [Verificação](#verificação)
*   [Soluções de Problemas](#soluções-de-problemas)
*   [Configuração do Ambiente de Desenvolvimento](#configuração-do-ambiente-de-desenvolvimento)

---

## Pré-requisitos de Ferramentas de Desenvolvimento

Este guia descreve os requisitos necessários para configurar as ferramentas em sistemas Windows e Linux, com links para instalação e orientações de configuração.

### Requisitos Gerais

- **Sistema Operacional**:
  - **Windows**: Versão 10 ou superior.
  - **Linux**: Qualquer distribuição recente (Ubuntu, Fedora, Debian, etc.).

- **Internet**: Conexão estável (Wi-Fi ou 4G).

### Ferramentas e Instalação

#### Java (JDK 21)
- **Windows**:
  - Baixe o JDK no site oficial da [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
  - Após a instalação, defina a variável de ambiente `JAVA_HOME`.

- **Linux**:
  - Execute no terminal:
    ```bash
    sudo apt update
    sudo apt install openjdk-21-jdk
    ```
  - Verifique a instalação com:
    ```bash
    java -version
    ```

#### Spring Boot
- Spring Boot requer o Java previamente instalado. A instalação é feita via Maven.
- **Guia de Instalação**: [Documentação oficial do Spring Boot](https://spring.io/guides).

#### Python 3
- **Windows**:
  - Baixe o instalador em [python.org](https://www.python.org/downloads/).
  - Marque a opção para adicionar o Python ao PATH durante a instalação.

- **Linux**:
  - Execute:
    ```bash
    sudo apt update
    sudo apt install python3
    ```
  - Verifique a instalação:
    ```bash
    python3 --version
    ```

#### Pip (Gerenciador de Pacotes Python)
- **Windows**:
  - Já vem incluso nas versões 3.x do Python.
  - Verifique com:
    ```bash
    pip --version
    ```

- **Linux**:
  - Instale com:
    ```bash
    sudo apt install python3-pip
    ```

#### Node.js (v21) e npm
- **Windows**:
  - Baixe do [site oficial do Node.js](https://nodejs.org/).
  - O npm é instalado automaticamente com o Node.js.

- **Linux**:
  - Instale com:
    ```bash
    sudo apt update
    sudo apt install -y nodejs npm
    ```
  - Verifique a instalação:
    ```bash
    node -v
    npm -v
    ```

#### MySQL
- **Windows**:
  - Baixe o instalador do [site oficial](https://dev.mysql.com/downloads/installer/).
  - Durante a instalação, selecione o modo "Developer Default" para incluir o MySQL Server e o Workbench.
  - Configure as credenciais do usuário root.

- **Linux**:
  - Instale o MySQL Server:
    ```bash
    sudo apt update
    sudo apt install mysql-server
    ```
  - Inicie e habilite o serviço:
    ```bash
    sudo systemctl start mysql
    sudo systemctl enable mysql
    ```
  - Execute a configuração segura:
    ```bash
    sudo mysql_secure_installation
    ```
  - Verifique:
    ```bash
    mysql --version
    ```

### IDEs e Ferramentas Recomendadas

### Visual Studio Code
- **Descrição**: Editor de código leve, personalizável e compatível com várias linguagens.
- **Download**: [VSCode](https://code.visualstudio.com/).
- **Extensões**: Python.

### MySQL Workbench
- **Descrição**: Ferramenta visual para modelagem, administração e desenvolvimento SQL.
- **Download**: [MySQL Workbench](https://dev.mysql.com/downloads/workbench/).

### IntelliJ IDEA
- **Descrição**: IDE robusta para desenvolvimento em Java, Spring Boot e outras tecnologias JVM.
- **Download**: [IntelliJ IDEA](https://www.jetbrains.com/idea/).

### PyCharm (Opcional)
- **Descrição**: IDE especializada para desenvolvimento Python.
- **Download**: [PyCharm](https://www.jetbrains.com/pycharm/).

### Ferramentas Adicionais
- Para desenvolvimento frontend, considere usar o **Figma** para design UI/UX: [Figma](https://www.figma.com/).
- Para edição de texto leve, utilize o **Notepad++**: [Notepad++](https://notepad-plus-plus.org/).

## Verificação

Após instalar as ferramentas necessárias, verifique suas instalações executando os seguintes comandos:

```bash
java -version
python3 --version
pip --version
node -v
npm -v
mysql --version
```

## Soluções de Problemas

Se você encontrar problemas durante a instalação ou verificação, siga os passos abaixo para resolver problemas comuns.

### Problemas com Java
- **Problema**: `java -version` não é reconhecido.
  - **Solução**: Verifique se o diretório `bin` do JDK foi adicionado ao PATH:
    - **Windows**: Adicione `C:\Program Files\Java\jdk-17\bin` à variável PATH.
    - **Linux**: Adicione `export PATH=$PATH:/usr/lib/jvm/java-17-openjdk/bin` ao `~/.bashrc` ou `~/.zshrc`, e execute `source ~/.bashrc`.

### Problemas com Python
- **Problema**: `python3 --version` não reconhecido.
  - **Solução**:
    - No **Windows**, verifique se o Python foi adicionado ao PATH durante a instalação.
    - No **Linux**, confirme a instalação com `sudo apt install python3`.

### Problemas com Pip
- **Problema**: Comando `pip` não encontrado.
  - **Solução**:
    - Execute `python3 -m ensurepip --upgrade` para instalar o pip.

### Problemas com Node.js ou npm
- **Problema**: Comandos `node` ou `npm` não reconhecidos.
  - **Solução**:
    - **Windows**: Reinstale o Node.js e certifique-se de marcar "Add to PATH" durante a configuração.
    - **Linux**: Instale usando o Node Version Manager (NVM) para melhor gerenciamento de versões:
      ```bash
      curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
      source ~/.bashrc
      nvm install 21
      ```

### Problemas com MySQL
- **Problema**: Não é possível iniciar o serviço MySQL.
  - **Solução**:
    - No **Linux**, verifique o status do serviço:
      ```bash
      sudo systemctl status mysql
      ```
      Se não estiver ativo, inicie-o:
      ```bash
      sudo systemctl start mysql
      ```

- **Problema**: Acesso negado para o usuário root.
  - **Solução**:
    - Execute o script de instalação segura para redefinir as credenciais:
      ```bash
      sudo mysql_secure_installation
      ```

### Problemas com PATH
- **Problema**: Comandos não reconhecidos globalmente.
  - **Solução**:
    - Verifique se o diretório `bin` da ferramenta foi adicionado ao PATH.
    - Reinicie seu terminal ou sistema após atualizar o PATH.

### Problemas com IDE
- **Problema**: A IDE não detecta as ferramentas instaladas.
  - **Solução**:
    - Verifique as configurações de caminhos da IDE:
      - Para PyCharm: Vá para **File > Settings > Project > Python Interpreter**.
      - Para IntelliJ IDEA: Vá para **File > Project Structure > SDKs** e adicione o JDK correto.

### Ajuda Adicional
- Visite a documentação oficial ou fóruns da comunidade para cada ferramenta:
  - [Java](https://www.oracle.com/java/technologies/)
  - [Python](https://www.python.org/)
  - [Node.js](https://nodejs.org/)
  - [MySQL](https://dev.mysql.com/doc/)

Se o problema persistir, considere reinstalar a ferramenta ou consultar uma comunidade de desenvolvimento para solução de problemas avançados.

---

## Configuração do Ambiente de Desenvolvimento

### 1. Banco de Dados
- Abra o MySQL Workbench.
- Configure uma conexão local na porta 3306.
- Crie um banco de dados chamado "_hardwaretechdb_".

### 2. BACKEND
- Clone o repositório [backend-api-REST](https://github.com/Azenith-Solutions/backend-api-rest).
- Crie um arquivo .env.development na mesma pasta de .env.production.
- Utilize o [.env.example](https://github.com/Azenith-Solutions/documentation-START-HERE/blob/main/.env.example) como referência para configurar as credenciais do banco, chave JWT e chave da API Brevo no arquivo .env.development.
- Execute o servidor backend.
- **Observação:** Verifique no MySQL Workbench se as tabelas foram criadas — o JPA deve gerá-las automaticamente a partir dos modelos.

### 3. Processo ETL
- Clone o repositório [excelDB_loader](https://github.com/Azenith-Solutions/extract-transform-load-script).
- Certifique-se de que o Python 3 esteja instalado.
- Garanta que o PIP esteja atualizado.
- Crie um arquivo .env na pasta raiz.
- Utilize o [.env.example](https://github.com/Azenith-Solutions/documentation-START-HERE/blob/main/.env.example) como referência para configurar as credenciais do banco e ambiente no arquivo .env.
- **Windows:**
  - Altere para o branch _windows_.
  - Instale as dependências:
```bash
pip install -r requirements.txt
```
  - Execute:
```bash
python main.py
```
- **Linux**:
  - Altere para o branch _main_.
- **Observação:** Verifique no MySQL se os dados foram inseridos corretamente.

### 4. FRONTEND
- Instale as dependências:
```bash
npm i
```
- Execute o frontend com Vite:
```bash
npm run dev
```
- **Observação:** Caso ocorra um erro, exclua o package-lock.json e a pasta node_modules, depois reinstale as dependências.

---

Para mais detalhes, consulte nossa [documentação](https://github.com/Azenith-Solutions/documentation-START-HERE) [principal](https://github.com/Azenith-Solutions/documentation-START-HERE).