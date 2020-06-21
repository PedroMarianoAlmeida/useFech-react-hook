# useFech-react-hook
Um react custom hook com objetivo de abstrair toda a etapa de requisitar dados para API externas

## Como usar:
### Formato da Declaração

Configuração inicial semelhante ao useState:

`const [ answerHook, setConfiguration ] = useFetch(myConfiguration);`

- A primeira variável já é o JSX para ser inserido no render
- A segunda variável é a função que fará realizar uma nova chamada, tem como parâmetro um Objeto com as configurações (explicado mais a frente)
- O parâmetro da função é o valor inicial do objeto (mesmo objeto da segunda variável, porém com valores modificados pelo usuário)

### Objeto de Configuração

A configuração inicial é um objeto com os seguintes parâmetros (valores dos parâmetros são exemplos):

- `url: "my URL",` - Obrigatório: String com o URL que será requisitada (todo o texto até imediatamente antes dos parâmetros)

-`parameters : [ { "nomeParâmetro": "ValorBuscado" } ],` - Opcional: Parâmetro passados para busca. O formato deve ser exatamente igual ao do exemplo: Uma array com cada elemento sendo um Objeto com um único parâmetro dentro.

- `shouldRun: true/false,` Opcional: Valor booleano que informa se a busca deve ocorrer ou não (e em caso de erro nos parametros url e shouldRun é passado automaticamente para false. Se não informado é setado como true

- `logResponses: true/false,` Opcional: Valor booleano que determina se o usuário que receber informações relevantes da etapa que o Hook está executando, recomendado ser usado durante etapa de desenvolvimento. Se não informado é setado como true

- `doWhenInactive: () => "",` Opcional: Função que retorna Elemento JSX que deve ser apresentado quando o Hook está configurado com o  `shouldRun = false,`. Se não informado é setado como "".

- `doWhenFetching: () => "",` Opcional: Função que retorna Elemento JSX que deve ser apresentado quando o Hook solicitou o Fectch porém ainda não houve resposta. Se não informado é setado como "".

- `doWhenSuccess: (rawAnswer) => <h1> { rawAnswer.param } </h1>,` Opcional: Função que retorna Elemento JSX que deve ser apresentado quando o Hook retorna com sucesso, o argumento da função é o Objeto retornado pelo Fetch. Se não informado aparece um lembrete na tela que o Hook não apresentará os dados na tela e seta logResponses para true (assim a resposta aparece no console.log)

- `doWhenFail: (error, rawAnswer) => <h1> {error.message} </h1>` Opcional: Função que retorna Elemento JSX que deve ser apresentado quando o Hook retorna com falha na busca do dado, os argumento da função são respectivamente a mensagem de erro e o objeto retornado (quando existente).

### Exemplos

[Modelo](https://github.com/PedroMarianoAlmeida/use-fetch-custom-hook) - Esse react app que foi usado para elaborar o hook, a aplicação não tem muita utilizada mas pode server de modelo de configuração.


