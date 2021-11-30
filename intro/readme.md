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

### Variáveis
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
  - Nossa "variável" de vetor definida, pode ser utilizada como função, como por exemplo
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
  - Se quisessemos poderíamos reatribuir o valor do "meu-vetor" para o novo vetor, estaríamos mudando o valor de referência da variável na memória
  Ex:
  ```clj
  (def meu-vetor (conj meu-vetor "Prando"))
  (println meu-vetor)
  // [Gabriel Prando Prando]
  ```

