# btime-back-test
## Cenário
Você deverá construir um verificador de condições.

Dado um conjunto de condições e um objetos a serem analisados, você deve retornar VERDADEIRO(em formato booleano) quando todas as condições forem satisfeitas e FALSO(em formato booleano) quando pelo menos uma condição não for satisfeita.

Exemplo de entrada:

```js 
{ 
  "name": "Pedro",
  "age": 35,
  "email": "pedro@pedro.com",
  "addressIds": [1,50,97],
  "documentIds": [1,5,19]
}
```

Exemplo de conjunto de condições:

```js 
[
  {
    "field": "name",
    "operator": "equal",
    "value": 10
  },
  {
    "field": "age",
    "operator": "ne",
    "value": 10
  },
  {
    "or":[
      {
        "field": "addressIds",
        "operator": "in",
        "value": [
          10,
          20,
          30
        ]
      },
      {
        "field": "documentIds",
        "operator": "nin",
        "value": [
          5,
          6,
          7
        ]
      }
    ]
  }
]
```

Cada condição do array irá seguir a seguinte estrutura:

```js
{
  "field": "name", // nome do campo a ser comparado
  "operator": "equal", // operador de verificação a ser utilizado
  "value": 10 // valor a ser comparado
}
```

Exemplo do esperado:

```ex
conditions = [...]
record = %{...}
# Deve retornar verdadeiro ou falso
verify(record, condition) 
```

## Operadores considerados:
 - "and" (combinar o conjunto de regras onde todas devem ser satisfeitas);
 - "or" (combinar o conjunto de regras de maneira que pelo menos UMA seja satisfeita);
 - "eq" (igualdade);
 - "ne" (diferente);
 - "in" (verifica se 1 ou mais itens estão contidos em um conjunto de valores);
 - "nin" (verifica se nenhum item está contido em um conjunto de valores).

## Considerações gerais:
 - Para combinar condições utilizando `or`, é preciso que a condição(`or`) esteja explícita no conjunto de condições;
 - As condições do conjunto de condições, quando o tipo de combinador (`or/and`) não for explicitamente informado, devem ser tratadas como `and`.
 - Se possível, incluá testes automatizados
