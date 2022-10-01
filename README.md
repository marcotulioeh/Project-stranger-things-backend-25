# Boas vindas ao repositório do projeto Stranger Things!

---

<details>
  <summary><strong>👨‍💻 O que deverá ser desenvolvido</strong></summary><br />

  Você vai adaptar e configurar os projetos descritos nesse README para que seja feito o deploy deles. Você vai colocar os projetos front-end e back-end no ar com o `Heroku`, utilizando o `Docker` em ambiente de produção. Além disso, você vai alterar alguns comportamentos aplicando os conceitos vistos no conteúdo. 

  ## Desenvolvimento

  Adapte e configure os projetos descritos nesse *README* para que seja feito o deploy utilizando `Docker` por meio do `Heroku`.

</details>

---

# Requisitos do projeto

⚠️ Lembre-se de que o seu projeto só será avaliado se estiver passando por **todos os _checks_** do **Linter**. Utilize o comando `npm run lint` no seu terminal para verificar os _checks_ do **Linter** 😉 ⚠️

Os requisitos estão agrupados por `frontend` e `backend`. Realize as alterações nos respectivos diretórios de cada repositório.

⚠️**IMPORTANTE**: Para esse projeto, as variáveis de ambiente devem ser definidas em um arquivo .env e o arquivo deve ser enviando no seu PR(Pull Request). ISSO NÃO É UMA PRÁTICA DE MERCADO, contexto no qual o arquivo .env deve ser sempre incluído no .gitignore, pois contém informações sensíveis. Aqui o arquivo .env será enviado apenas por motivo de avaliação.

---

## O teste no back-end:

### 1 - Verifica as variáveis de ambiente

<details>
  <summary>
    Altere o back-end para utilizar variáveis de ambiente para controlar a <b>porta</b> em que API escutará e o <b>modo</b> "upsideDown".
  </summary><br/>
  
  1. A porta que a API escutará, essa variável deve ter, necessariamente, o nome PORT e o seu valor deve ser 3000.

  2. O modo "upsideDown". Essa variável espera um valor boleano e deverá se chamar UPSIDEDOWN_MODE. Lembre-se de que as variáveis de ambiente são `strings`.
  O que será testado:
  - Se existe a variável de ambiente PORT;
  - Se a variável de ambiente UPSIDEDOWN_MODE existe e se ela é um boleano.

</details>

### 2 - Verifica se o arquivo Dockerfile está configurado da maneira correta

<details>
  <summary>
    O teste irá verificar se o arquivo `Dockerfile` existe e está configurado da maneira correta. Ele deve construir a imagem a partir da `node:14-alpine` e usar o comando `npm start` para iniciar a aplicação via `CMD`.
  </summary><br/>

  O que será testado:

  - Se o Dockerfile está utilizando a imagem `node:14-alpine`, verificando se as camadas dessa imagem estão incluídas no build que esse Dockerfile faz;

  - Se o Dockerfile usa `npm start` como `CMD`.

</details>

### 3 - Verifica se o arquivo heroku.yml está configurado na maneira correta

<details>
  <summary>
    Adicione e configure o arquivo <code>heroku.yml</code>.
  </summary><br/>

  1. O arquivo deve iniciar um servidor do tipo `web`;

  2. O `run` deve executar o servidor utilizando o `node`.

  Execute ambos na sua máquina para validar se o comportamento é o esperado.

  O que será testado:

    - Se o arquivo `heroku.yml` existe;

    - Se o serviço a ser executado é um serviço do tipo `web`;

    - Se o `node` é responsável por executar o servidor.

</details>

### 4 - Verifica action de Linter para ser executada no GitHub

<details>
  <summary>
    Você deverá criar uma <code>Action</code> para ser executada somente em **pull_requests** solicitados em todas as branches de seu repositório.
  </summary><br/>
  
  **Atenção**: O arquivo de configuração da action deverá ser criado em: `./actions/` com o nome `project.yml`.
  
  O que será validado:
  
  - Se o arquivo `project.yml` existe na pasta `actions`;
  
  - Se a Action será executada somente em pull requests;

  - Se o job foi nomeado como `eslint`;

  - Se o job `eslint` é executado com a versão **20.04** do ubuntu;

  - Se o primeiro passo do job `eslint` usa a action de **checkout**;
  
  - Se o segundo passo do job `eslint` usa a action de **setup-node** e sua versão é a `12`;

  - Se no terceiro passo do job o `eslint` executa a instalação das dependências;

  - Se o quarto passo do job `eslint` executa o pacote `eslint` via `npx`;


**Dica**: Dê uma olhada na [documentação de actions do github](https://docs.github.com/pt/actions/learn-github-actions/understanding-github-actions);

</details>

### 5 - Verifica o Deploy no Heroku

<details>
  <summary>
    Crie dois apps para a API: um para o o app <code>hawkins</code> e outro para o app <code>upside-down</code>.
  </summary><br/>

  ⚠️**IMPORTANTE**: Uma variável de ambiente com o nome `GITHUB_USER` deverá ser criada em seu `.env` com o **seu nome de pessoa usuária** do GitHub.

  ⚠️**IMPORTANTE**: 
 - O Heroku limita o tamanho do nome de uma aplicação para ter no máximo **30 caracteres** contendo apenas letras minúsculas:
    - se o seu nome de pessoa usuária do GitHub possuir mais do que **27 caracteres**, ou contenha **letras maiúsculas**, ou **comece com um número**, você não conseguirá criar uma aplicação com o nome no padrão solicitado pelo requisito. 
    - você pode usar uma abreviação do seu `GITHUB_USER` apenas com letras minúsculas na variável de ambiente e criar o `app` com o mesmo pré-fixo, por exemplo, temos o seguinte nome do github, `tryber-com-nome-de-github-maior-que-27-caracteres`:
```sh
GITHUB_USER=tryber
# E o nome dos apps deveriam ficariam assim:
# tryber-up - para o app hawkins;
# tryber-dw - para o app upside-down.
```


  1. Crie dois `apps` do Heroku a partir do mesmo código fonte (código da API). O nome do seu app no Heroku deverá conter o seu nome de pessoa usuária no GitHub seguido de "-up" e "-dw". Por exemplo, se seu nome de pessoa usuária no GitHub for "student", seus apps deverão ter os nomes "student-up" e "student-dw" e as URLs abaixo:

    - https://student-up.herokuapp.com/ - para o app hawkins;

    - https://student-dw.herokuapp.com/ - para o app upside-down.

  2. Configure a variável de ambiente criada para controlar o modo `UPSIDEDOWN`. Cada um dos `apps` deverá ter valores distintos, da seguinte maneira:

    - O app `hawkins` deverá ter o valor `false`;

    - O app `upside-down` deverá ter o valor `true`.

  3. Utilizando o `git`, faça o deploy de ambos os `apps` no Heroku.

  Acesse as URLs geradas e valide se ambas as API's estão no ar e funcionando como esperado.

  ⚠️ **IMPORTANTE**: As URLs deverão ser geradas pelo Heroku e não devem ser modificadas.

  **O que será testado**:
    - Se ao fazer uma requisição do tipo GET para o endpoint da API hawkins serão retornadas as informações corretas;

    - Se ao fazer uma requisição do tipo GET para o endpoint da API upside-down serão retornadas as informações corretas.
</details>

---
