# Artigo Instanciação

**Autor:** Marcelo H M Dias

## Hoisting

Em JavaScript *hoisting* é a elevação/hasteamento das declarações de funções e/ou variáveis para o topo do escopo. Isso ocorre devido a prioridade no processamento antes da execução do código.

```javascript
bar = 10;

function foo () {
	// Função imprime variável inicializada antes da declaração
	console.log(bar);
}

var bar; // Variável declarada após a inicialização.

foo(); // Irá imprimir o valor da variável

console.log(bar + 1); // Impime o valor da soma: 11
```

Porém, no caso de variáveis, apenas a declaração é *hoisted*, não sua inicialização.

```javascript
console.log(foo); //Console imprime undefined

var foo = 5; // Váriavel é declarada e inicializada

console.log(foo); // Imprime o valor de foo: 5
```

No exemplo anterior, o valor é impresso como *undefined*, pois `foo` já existe no escopo, apenas não possui um valor atribuido.

Já para funções o hasteamento ocorre de forma diferente. Toda a estrutura é *hoisted*, e não só seu nome.

```javascript
function foo(){
  function bar() {
    return 3
  }

  return bar()

  function bar() {
    return 8
  }
}

console.log(foo())

//Exemplo retirado do site Loop Infinito
```

Neste exemplo o retorno da função `foo()` é `8` issó ocorre, pois a segunda função `bar()` sobrescreve a primeira e como as duas passam pelo hasteamento há a sobreposição de valor.

Para funções declaradas como expressão `var foo = function () {...}` a regra é a mesma das variáveis, o *hoisting* ocorre apenas na declaração da variável, não no seu conteúdo.

## Closure

Closure (fechamento) são funções que referenciam variáveis intependentes a ela, ou seja, variáveis que se encontram em outro escopo.

```javascript
function init() {
  var name = "Mozilla";
  function displayName() {
    alert(name);
  }
  displayName();
}
init();

// Exemplo retirado do site mozila.org
```

Neste exemplo a variável `name` não foi declarada no mesmo escopo de onde está sendo utilizada `alert(name)`, porém a função `displayName()` tem acesso a ela através da *Closure*.




## Variável Global

## Variável por parâmetro

## Instanciação usando uma IIFE

