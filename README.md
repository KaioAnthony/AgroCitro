# Grupo:Leonardo Augusto de Souza Silva, Kaio Anthony Alves de Oliveira, Isaac Iuri Alves de Oliveira, Maria Clara Silva Galindo

## AgroCitro


O **AgroCitro** é um sistema web voltado para o **gerenciamento de atividades agrícolas**, integrando páginas dinâmicas (**HTML, CSS e JavaScript**), um **servidor Node.js** e um **banco de dados SQL** para armazenamento de informações.

Este guia passo a passo cobrirá a configuração do ambiente, a instalação das dependências, a configuração do banco de dados e a inicialização do servidor, garantindo que sua aplicação Node.js e Express funcione corretamente.

## Pré-requisitos

Para rodar esta aplicação, você deve ter instalado:

- [Node.js](https://nodejs.org/) (e, por consequência, o npm - Node Package Manager).
- Um servidor de banco de dados [MySQL](https://www.mysql.com/) ou [MariaDB](https://mariadb.org/).

Aqui está o conteúdo em formato Markdown (`README.md`):

````markdown
# Sistema de Gerenciamento de Plantio, Irrigação e Colheita

Esta aplicação backend é desenvolvida com Node.js e Express, projetada para gerenciar as operações de plantio, irrigação e colheita de um sistema agrícola. O servidor usa os drivers `mysql` e `mysql2` para se conectar a um banco de dados relacional e executar operações de CRUD (Create, Read, Update, Delete) através das rotas da API.

##  Pré-requisitos

Antes de rodar a aplicação, certifique-se de ter os seguintes pré-requisitos instalados:

- [Node.js](https://nodejs.org/) (inclui o npm - Node Package Manager).
- Um servidor de banco de dados [MySQL](https://www.mysql.com/) ou [MariaDB](https://mariadb.org/).

## Configuração e Instalação

### Passo 1: Obter os Arquivos

Certifique-se de que os arquivos `package.json`, `server.js` e a pasta `repositorio` (contendo o arquivo `bancoDados.js`) estão na mesma pasta.

### Passo 2: Instalar Dependências

No terminal, navegue até o diretório do projeto e execute o comando para instalar as dependências:

```bash
npm install
````

As dependências instaladas serão:

* `express`
* `mysql`
* `mysql2`

### Passo 3: Configurar o Banco de Dados

**Atenção:** O código depende de um arquivo de módulo de banco de dados (`./repositorio/bancoDados.js`), que não foi incluído, mas é essencial para a conexão.

#### Criação do Banco

Crie o banco de dados no seu servidor MySQL:

```sql
CREATE DATABASE farm_manager;
```

#### Configuração da Conexão

Configure as credenciais de conexão (host, usuário, senha, nome do banco) dentro do arquivo `./repositorio/bancoDados.js`.

#### Implementação das Funções

O arquivo `bancoDados.js` deve conter e exportar as funções utilizadas pelo `server.js`, como:

* `obterPlantios`
* `incluirPlantios`
* `obterTotalMudas`
* `obterIrrigacao`
* `incluirIrrigacao`
* `obterColheita`
* `incluirColheita`

#### Estrutura das Tabelas

Garanta que as tabelas necessárias (por exemplo: `Plantios`, `Irrigacao`, `Colheita`) estejam criadas no banco de dados para que as queries SQL executadas pelas funções não falhem.

### Passo 4: Inicializar o Servidor

Com as dependências instaladas e o banco de dados configurado, inicie o servidor com o script definido no `package.json`:

```bash
npm start
```

Ou, alternativamente, execute diretamente o arquivo:

```bash
node server.js
```

Se a inicialização for bem-sucedida, você verá a seguinte mensagem no terminal:

```
Servidor OnLine!
O servidor estará escutando na porta 3000.
```

## Rotas da API (Endpoints)

A aplicação expõe os seguintes endpoints HTTP, rodando em `localhost:3000`:

| Método | Endpoint            | Descrição                                                | Dados Necessários (Body JSON)                                 |
| ------ | ------------------- | -------------------------------------------------------- | ------------------------------------------------------------- |
| GET    | /plantios           | Retorna a lista de todos os registros de plantio.        | N/A                                                           |
| POST   | /registrarPlantio   | Registra um novo plantio no banco de dados.              | `{Variedade, Data_Plantio, Quantidade_Plantada, Localizacao}` |
| GET    | /mudas              | Retorna o total de mudas e a data da última atualização. | N/A                                                           |
| GET    | /irrigacao          | Retorna a lista de todos os registros de irrigação.      | N/A                                                           |
| POST   | /registrarIrrigacao | Registra uma nova sessão de irrigação.                   | `{ID_Plantio, Horario_Inicial, Horario_Final}`                |
| GET    | /colheita           | Retorna a lista de todos os registros de colheita.       | N/A                                                           |
| POST   | /registrarColheita  | Registra uma nova colheita para um plantio.              | `{ID_Plantio, Data_Colheita, Quantidade_Colhida, Qualidade}`  |

##  Exportar para as Planilhas

### Testando a API

Você pode testar essas rotas usando ferramentas de desenvolvimento como [Postman](https://www.postman.com/), [Insomnia](https://insomnia.rest/) ou `curl`.

#### Exemplo de Sucesso para POST (em todas as rotas de registro):

```json
{
    "msg": "Atualizado!"
}
```

#### Exemplo de Falha na Rota `/registrarIrrigacao` (se faltar algum campo):

```json
{
    "msg": "Todos os campos são obrigatórios."
}
```

## Notas Adicionais

* **Banco de Dados**: O arquivo `bancoDados.js` contém as funções de interação com o banco de dados. Certifique-se de que todas as funções necessárias estão implementadas e que a conexão ao banco de dados está configurada corretamente.
* **Dependências**: As bibliotecas essenciais são o `express`, que gerencia o servidor HTTP, e `mysql2` para a conexão e execução das queries SQL no banco de dados.
* **CORS**: Caso deseje permitir acessos externos (por exemplo, de uma frontend hospedada em outro servidor), você pode precisar configurar o [CORS](https://expressjs.com/en/resources/middleware/cors.html) no Express.

---

Obrigado por usar o **Sistema de Gerenciamento de Plantio, Irrigação e Colheita**! Se você tiver dúvidas ou sugestões, sinta-se à vontade para abrir uma issue ou enviar um pull request!

## Resumo do que foi incluído:

* **Introdução e objetivos** do projeto.
* **Pré-requisitos** e como instalá-los.
* **Passo a passo detalhado** de como configurar e rodar a aplicação, incluindo a configuração do banco de dados.
* **Endpoints da API** com a descrição e os dados necessários.
* **Exemplos de sucesso e erro** para ajudar na validação das rotas.

Agora o documento está completo e organizado, pronto para ser utilizado como um `README.md` no seu repositório!

```

Esse é o formato Markdown para o seu arquivo `README.md`, pronto para ser utilizado no seu repositório.
```

