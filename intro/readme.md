# Clojure
- Linguagem funcional
- Roda na JVM
- Clojure tem suporte para sequências preguiçosas (lazy sequences) e incentiva o princípio da imutabilidade e estruturas de dados persistentes.
- Clojure suporta funções como objetos de primeira classe, um console interpretador (repl), e um sistema de macros.
- Clojure é construída em expressões simbólicas que são primeiramente analisadas ​​em estruturas de dados por um leitor, antes de serem efetivamente compiladas.
- O leitor da linguagem Clojure suporta a sintaxe literal para mapas, conjuntos e vetores, além de listas, e estes são compilados para as estruturas citadas diretamente.
- O código Clojure é executado na máquina virtual Java e como resultado se integra com o ambiente Java permitindo invocar código Java a partir do código Clojure, assim como código Clojure também pode ser invocado a partir de código Java
  
## Instalação
- [Link oficial](https://clojure.org/guides/getting_started)

## Tirando a maldição

> Acesse o interpretador do clojure digitando "clj" no seu terminal

```clj
(println "Hello world!")
```

## Invocações 
- Toda invocação de função no clojure deve estar em volta de parênteses
- Dentro dos parênteses, o primeiro "parâmetro" que temos é o nome da função que queremos invocar  
  Ex: 
    ```clj
      (println "Hello world!")
    # [ func ] [ parâmetros ]
    
      (+ 1 2) // 3
    ```

## Definição de símbolos
- Símbolos são como se fossem nossas variáveis  

### Símbolos
  Ex: 
  ```clj
      (def meu-nome "Gabriel")
      (println meu-nome) 
      // Gabriel
  ```

### Vetores
  Ex:  
  ```clj
      (def meu-vetor ["Gabriel", "Prando"])
      (println meu-vetor) 
      // [Gabriel Prando]
  ```
  - No print temos os elementos sem as aspas da string e sem vírgula, devido ao clojure tratar a vírgula como um espaço, logo a nossa definição poderia ser da seguinte forma:  
 
  ```clj
      (def meu-vetor ["Gabriel" "Prando"])
      (println meu-vetor) 
      // [Gabriel Prando]
  ```
  - Nossa símbolo ("variável") de vetor definida, pode ser utilizada como função, como por exemplo
  ```clj
    (meu-vetor 0) 
    // "Gabriel"
  ```
  - Se quisermos saber quantos elementos temos em "meu-vetor"
  ```clj
    (count meu-vetor)
    // 2
  ```
  - Se quisermos adicionar um elemento no "meu-vetor"
  ```clj
    (conj meu-vetor "Prando")
    // ["Gabriel" "Prando" "Prando"]
  ```
  - Agora ao imprimir "meu-vetor", teremos o resultado ["Gabriel" "Prando" "Prando"] ? ***Não***, ai entra um ponto importante do clojure, devido a ***imutabilidade*** a função conj não altera o valor do vetor, ela retorna um novo vetor com o vetor original + valor adicionado
  - "*Quando estamos trabalhando com valores imutáveis, podemos passá-los para qualquer pessoa sem medo que a função invocada vá alterá-lo de alguma forma, nos permitindo um controle maior sobre o nosso código. Essa é uma dentre as muitas vantagens da imutabilidade.*"
  - Se quisessemos poderíamos reatribuir o valor do "meu-vetor" para o novo vetor, estaríamos mudando o valor de referência desse símbolo na memória
  Ex:
  ```clj
  (def meu-vetor (conj meu-vetor "Prando"))
  (println meu-vetor)
  // [Gabriel Prando Prando]
  ```

### Definição de função
- Usamos a tag defn, seguido do nome da função e seus parâmetros  
  Ex: 
```clj
(defn imprime-mensagem []
  (println "Hello World!"))

(imprime-mensagem)
// Hello World!
```
- Podemos receber parâmetros
  Ex: 
```clj
(defn imprime-mensagem [nome-pessoa]
  (println "Hello" nome-pessoa))

(imprime-mensagem "Gabriel")
// Hello Gabriel
```

### Definição de símbolo dentro de uma função
```clj
(defn valor-descontado
  "Retorna o valor com desconto de 10%."
  [valor-bruto]
  (def desconto 0.10)
  (* valor-bruto (- 1 desconto)))
```
- Ao usar a definição com ***def*** o símbolo se torna global dentro do namaspace, o que é péssimo, pois pode ocasionar grandes colisões com outros possíveis simbolos de mesmo nome, para evitar isso podemos declarar símbolos de escopo a nível de função

```clj
(defn valor-descontado
  "Retorna o valor com desconto de 10%."
  [valor-bruto]
  (let [desconto 0.10]
  (* valor-bruto (- 1 desconto))
 )
)

(valor-descontado 100)
```
- Como tudo é função, temos que declarar ***let*** dentro da mesma função de iremos utilizar, após a declaração do símbolo, podemos passar como parâmetro outra função que vai ser executada, como no exemplo a cima 

### Múltiplas declarações no let
- Podemos declarar mais do que um let no mesmo declaração, recebemos um vetor de declarações

```clj
(defn valor-descontado
  "Retorna o valor com desconto de 10%."
  [valor-bruto]
  (let [taxa-de-desconto (/ 10 100)
        desconto (* valor-bruto taxa-de-desconto)]
    (println "Calculando desconto de" desconto)
    (* valor-bruto (- valor-bruto desconto))))
```
- Repare que temos a declaração do ***taxa-de-desconto*** e na sequência ***desconto***

## Condicionais
- ***if*** é uma forma, não é uma função, e é uma forma especial https://clojure.org/reference/special_forms#if. Na prática, formas especiais podem ser utilizadas em nosso código e se misturam com as funções que invocamos em diversos momentos. Em geral, serão formas especiais aquelas que formam a base mínima da linguagem, uma maneira tradicional que as linguagens encontram para que a maior parte da mesma seja implementada na própria linguagem.
- Ao utilizar o ***if*** o primeiro parâmetro é o simbolo if com a segunda expressão verdadeira ou falsa, terceira execução caso verdadeiro e quarto parâmetro caso contrário ***else*** 

```clj
(if true "é verdadeiro" "é falso")
```


```clj
(if (> 100 50) (println "100 é maior do que 50") (println "100 é menor do que 50"))
```