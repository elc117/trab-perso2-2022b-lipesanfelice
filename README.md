![Haskell](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTg61vJVPrOS4aw-jcRr0cm2MD_QFYbvs1n98V2OQcWBetmhgO12dSz2zQKuM5Taf8jFN8&usqp=CAU)

# Pattern Matching em Haskell

* O pattern matching é uma técnica de programação utilizada para comparar uma entrada (geralmente uma string ou expressão regular) com um conjunto de padrões pré-definidos e, em caso de correspondência, executar uma ação específica. É comumente utilizado em linguagens de programação funcionais, como Haskell e Erlang, mas também pode ser encontrado em outras linguagens como C, C++, Python, e Java.

## Existem vários tipos de pattern matching, cada um com suas próprias características e usos. Alguns exemplos incluem:
* Padrões de expressão regular: onde a entrada é comparada com uma expressão regular específica e, em caso de correspondência, uma ação é executada.
* Padrões de estrutura de dados: onde a entrada é comparada com uma estrutura de dados específica, como uma tupla ou uma lista, e, em caso de correspondência, uma ação é executada.
* Padrões de tipo: onde a entrada é comparada com um tipo específico, como um número inteiro ou uma string, e, em caso de correspondência, uma ação é executada.

######
* O pattern matching é útil em várias situações, como a validação de entrada de dados, a análise de expressões matemáticas e a manipulação de estruturas de dados complexas. Ele também pode ser combinado com outras técnicas de programação, como recursão e programação orientada a objetos, para criar soluções de programação mais elegantes e eficientes.
* Além disso, o pattern matching pode ser utilizado para garantir a coerência de tipos, evitando erros na execução do código. Além disso, o pattern matching também pode ser utilizado para destruturar estruturas de dados, tornando acesso aos seus dados mais fácil e menos verboso.
* É uma técnica de programação poderosa e versátil que permite comparar entradas com padrões pré-definidos e executar ações específicas em caso de correspondência. Ele é comumente utilizado em linguagens funcionais, mas também pode ser encontrado em outras linguagens. Ele pode ser usado para validação de dados, análise de expressões matemáticas, manipulação de estruturas de dados complexas e garantir coerência de tipos.
* Pattern matching é uma técnica utilizada em Haskell para comparar valores de diferentes tipos de dados e, dependendo da correspondência, executar uma ação específica. Ele é muito útil para escrever código simples e conciso, pois permite que você trate diferentes casos de forma clara e organizada. Ele é amplamente utilizado em funções de alta ordem, como map, filter e fold, bem como em estruturas de dados como listas e tuplas.

## Alguns exemplos de como o pattern matching pode ser usado em diferentes aplicações em Haskell:

### 1. Verificação de tipos:

```
data Shape = Circle Float | Rectangle Float Float

area :: Shape -> Float
area (Circle r) = pi * r^2
area (Rectangle l w) = l * w
```

* Essa função define uma tipo de dados chamado Shape, que pode ser um Circle (círculo) ou um Rectangle (retângulo) e uma função chamada area que calcula a área de uma forma.
* A função area usa pattern matching para verificar se a forma é um Circle ou um Rectangle. Se for um Circle, a função calcula a área do círculo como pi * r^2, onde r é o raio do círculo. Se for um Rectangle, a função calcula a área do retângulo como l * w, onde l é a largura e w é a altura do retângulo.

### 2.	Desconstrução de tuplas:

```
addVectors :: (Double, Double) -> (Double, Double) -> (Double, Double)
addVectors (x1, y1) (x2, y2) = (x1 + x2, y1 + y2)
```

* Essa função define uma função chamada addVectors que adiciona dois vetores. Ela usa pattern matching para desestruturar os dois vetores (x1, y1) e (x2, y2) passados como argumento.
* Em seguida, a função adiciona os componentes x de cada vetor e os componentes y de cada vetor para obter os componentes x e y do vetor resultante. Por fim, ela retorna o vetor resultante como uma tupla (x1+x2, y1+y2).

### 3. Verificação de listas:

```
head' :: [a] -> a
head' [] = error "List is empty"
head' (x:_) = x
```

* Esta função define uma função chamada head' que retorna o primeiro elemento de uma lista. Ela usa pattern matching para verificar se a lista passada como argumento é vazia ou não.
* Se a lista for vazia, a função retorna um erro "List is empty". Caso contrário, ela desestrutura a lista usando o operador (:) e retorna o primeiro elemento x. Isso é feito usando "_" que descarta o resto dos elementos da lista.

### 4.	Verificação de char:

```
isVowel :: Char -> Bool
isVowel 'a' = True
isVowel 'e' = True
isVowel 'i' = True
isVowel 'o' = True
isVowel 'u' = True
isVowel _ = False
```

* Esta função define uma função chamada isVowel que retorna se um caractere é uma vogal ou não. Ela usa pattern matching para comparar o caractere passado como argumento com cada uma das vogais possíveis. Se o caractere for igual a 'a', 'e', 'i', 'o' ou 'u' a função retorna True, caso contrário, retorna False. Isso é feito através do uso do "_" que é usado para descartar qualquer outro valor que não esteja listado nas condições.

### 5.	Verificação recursiva:

```
length' :: [a] -> Int
length' [] = 0
length' (_:xs) = 1 + length' xs
```

* Este é um exemplo de uma função recursiva que utiliza o pattern matching para calcular o comprimento de uma lista. A função toma uma lista de qualquer tipo como entrada e retorna um Inteiro. A primeira cláusula de pattern matching verifica se a lista é vazia, caso verdadeiro, retorna 0. A segunda cláusula de pattern matching descompacta o primeiro elemento da lista e chama recursivamente a função com o resto da lista. A cada chamada recursiva, 1 é adicionado ao resultado e retornado quando todos os elementos da lista tiverem sido processados. O pattern matching é utilizado para garantir que a função funcione corretamente para qualquer tipo de lista, sem importar se é vazia ou não.

### 6.	Verificação de valores:

```
factorial :: Int -> Int
factorial 0 = 1
factorial n = n * factorial (n-1)
```

* Essa função "factorial" é uma função recursiva que calcula o fatorial de um número inteiro. Ela usa o pattern matching para verificar se o número passado é igual a 0. Se for, ela retorna 1. Caso contrário, ela chama a si mesma passando n-1 e multiplica o resultado pelo número passado. O pattern matching é usado para ajudar a definir as condições de parada da recursão e as etapas que precisam ser tomadas para chegar ao resultado final.

### 7.	Verificação com guardas:

```
max' :: (Ord a) => a -> a -> a
max' a b
    | a > b     = a
    | otherwise = b
```

* Uma função que recebe dois argumentos de tipo 'a' que é instanciado com o typeclass Ord. A função compara se o primeiro argumento é maior que o segundo e, se for, retorna o primeiro argumento, caso contrário, retorna o segundo argumento. A função usa pattern matching para comparar os dois argumentos e determinar qual deve ser retornado.

### 8.	Verificação de where:

```
cylinder :: (RealFloat a) => a -> a -> a
cylinder r h =
    let sideArea = 2 * pi * r * h
        topArea = pi * r ^ 2
    in  sideArea + 2 * topArea
```

* Este exemplo mostra como usar Pattern matching com as funções de uma estrutura de dados específica, no caso, "cylinder". Ele define uma função "cylinder" que recebe três argumentos, dois reais e um inteiro. Essa função usa o let para definir duas variáveis, "sideArea" e "topArea", que são usadas para calcular a área lateral e a área superior de um cilindro, respectivamente. Em seguida, o "in" é usado para retornar o resultado da soma das duas áreas.

### 9.	Verificação de case:

```
describeList :: [a] -> String
describeList ls = "The list is " ++ case ls of [] -> "empty."
                                               [x] -> "a singleton list."
                                               xs -> "a longer list."
```

* A função describeList recebe uma lista de qualquer tipo e retorna uma string descrevendo a lista. Ela usa uma declaração "case" para verificar os diferentes padrões possíveis da lista de entrada. Se a lista estiver vazia, ela retorna a string "The list is empty." (A lista é vazia). Se a lista tiver apenas um elemento, ela retorna a string "The list is a singleton list." (A lista é uma lista de um único elemento). Se a lista tiver mais de um elemento, ela retorna a string "The list is a longer list." (A lista é uma lista mais longa).

### 10. Verificação de função:

```
capital :: String -> String
capital "" = "Empty string, whoops!"	
capital all@(x:xs) = "The first letter of " ++ all ++ " is " ++ [x]
```

* A função capital recebe uma string como entrada e retorna uma string. Ela usa o recurso de atribuição de variável com @ para atribuir a string inteira a uma variável all e a primeira letra a uma variável x. Se a string for vazia, ela retorna a string "Empty string, whoops!". Caso contrário, ela retorna a string "The first letter of " seguida da string original "all" e " is " seguido pela primeira letra da string original x.

### 11.	Verificação de função recursiva:

```
replicate' :: Int -> a -> [a]
replicate' n x
    | n <= 0    = []
    | otherwise = x : replicate' (n-1) x
```

* A função replicate' recebe um inteiro n e um valor x, e retorna uma lista contendo n cópias do valor x. Se n for menor ou igual a 0, a função retorna uma lista vazia. Caso contrário, a função retorna uma lista com x como o primeiro elemento e as n-1 cópias de x obtidas pela chamada recursiva da função replicate' (n-1) x.

### 12.	Verificação de estruturas de dados:

```
data Tree a = Leaf a | Node (Tree a) (Tree a)

treeSum :: Tree Int -> Int
treeSum (Leaf x) = x
treeSum (Node l r) = treeSum l + treeSum r
```

* A função treeSum é utilizada para calcular a soma de todos os elementos de uma árvore de inteiros. Ela utiliza recursão para percorrer a árvore e somar cada elemento. Se o nó é uma folha (Leaf), a função retorna o valor contido nela. Se o nó é um nó interno (Node), a função chama recursivamente treeSum para os dois filhos do nó e soma os valores retornados.

### 13. Verificação de funções de alta ordem:

```
zipWith' :: (a -> b -> c) -> [a] -> [b] -> [c]
zipWith' _ [] _ = []
zipWith' _ _ [] = []
zipWith' f (x:xs) (y:ys) = f x y : zipWith' f xs ys
```

* No corpo da função zipWith', o pattern matching é usado para corresponder às entradas de lista [a] e [b]. Ele permite que a função se comporte de maneira diferente dependendo do formato das entradas.
* Quando a primeira lista é esvaziada ([]) ou a segunda lista é esvaziada, a função retorna uma lista vazia. Caso contrário, a função aplica a função f ao primeiro elemento da primeira lista e o primeiro elemento da segunda lista, e concatena esse resultado com o resultado da chamada recursiva da função com as listas restantes. Assim, o pattern matching permite a função tratar casos especiais de entrada e evitar erros, enquanto também fornece uma maneira concisa de manipular as entradas.

### 14.	Verificação de funções polimórficas:

```
applyTwice :: (a -> a) -> a -> a
applyTwice f x = f (f x)
```

* Essa função utiliza o pattern matching para aplicar uma função dada (f) duas vezes a um determinado valor (x). A função applyTwice toma uma função (a-> a) e um valor (a) como entrada. Ela usa o pattern matching para aplicar a função dada duas vezes sobre o valor.
* A primeira vez, a função é aplicada a x e o resultado é armazenado na variável fx. A segunda vez, a função é aplicada novamente a fx e o resultado final é retornado. Dessa forma, a função applyTwice permite que uma função dada seja aplicada duas vezes consecutivas a um valor específico.

### 15.	Verificação de funções recursivas com casos base e recursão:

```
fibonacci :: Int -> Int
fibonacci 0 = 0
fibonacci 1 = 1
fibonacci n = fibonacci (n-1) + fibonacci (n-2)
```

* Essa função calcula o n-ésimo número de Fibonacci usando o pattern matching. Ela recebe um número inteiro n como entrada e retorna o n-ésimo número de Fibonacci.
* A primeira cláusula de pattern matching verifica se o n é igual a 0, se sim, a função retorna 0. A segunda cláusula verifica se o n é igual a 1, se sim, a função retorna 1. A terceira cláusula é chamada quando n é maior do que 1, neste caso, a função usa recursão para calcular o n-ésimo número de Fibonacci como a soma dos (n-1) e (n-2) números de Fibonacci.

### 16.	Verificação de tipos de dados personalizados:

```
data Person = Person { firstName :: String, lastName :: String, age :: Int }
	
greet :: Person -> String
greet (Person f l a) = "Hello, " ++ f ++ " " ++ l ++ "! You are " ++ show a ++ " years old."
```

* Essa função define um tipo de dados Person que contém três campos: firstName, lastName e age. Depois, ela define uma função greet que recebe uma pessoa como entrada e retorna uma string de saudação.
* A função greet usa pattern matching para descompactar a pessoa e extrair os campos firstName, lastName e age. Ela então usa esses campos para construir uma string de saudação "Hello, [firstName] [lastName]! You are [age] years old." e retorna essa string.

### 17.	Verificação de tipos de dados parametrizados:

```
f :: (Num a) => a -> String
f x = case x of
  0 -> "zero"
  1 -> "um"
  _ -> "outro número"

```
* Neste exemplo, a função f aceita um parâmetro x que é do tipo numérico a (que é parametrizado pelo tipo). O pattern matching é realizado usando a sintaxe case x of, que verifica o valor de x e retorna uma string correspondente. Se x for igual a 0, a string "zero" é retornada. Se x for igual a 1, a string "um" é retornada. Em outros casos, a string "outro número" é retornada.

### 18.	Verificação de estruturas de dados infinitas:

```
takeN :: Int -> [a] -> [a]
takeN 0 _ = []
takeN n (x:xs) = x : takeN (n - 1) xs

-- | Define uma lista infinita de números pares
pares :: [Int]
pares = map (*2) [0..]
```

*  Nesse exemplo, a função takeN utiliza o padrão de casamento para verificar se a quantidade desejada de elementos (n) é zero. Se for, a lista retornada será vazia. Se não for, o primeiro elemento da lista de entrada é adicionado à lista retornada e a chamada recursiva é feita com n decrementado em 1. A lista pares é uma lista infinita de números pares, criada usando a função map para aplicar a multiplicação por 2 a cada elemento da lista de inteiros de 0 a infinito. A função main lê a quantidade desejada de números pares a partir da entrada do usuário e chama a função takeN para obter essa quantidade da lista infinita pares.

## Link do Repl.it
* [Trabalho2](https://replit.com/@FelipeSanfelice/Trabalho-individual-2-Paradigmas-de-programacao)

# Referências 
* [learnyouahaskell](http://learnyouahaskell.com/)
* [Haskell](https://www.haskell.org/)
* [WikiBooks](https://en.wikibooks.org/)
* https://www.youtube.com/watch?v=SnnUKVU5BOA
* https://www.youtube.com/watch?v=Y1s28Sm5s8E

