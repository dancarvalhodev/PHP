# 5.6 - 7.0

# Modificações na manipulação de erros e exceções
Alguns erros fatais e recuperáveis foram convertidos para exceções no PHP 7. 

# Construtores internos sempre lançarão exceções em caso de falha
Todas as classes internas agora lançam Exception, da mesma forma que classes de usuário já faziam. 

# Mudanças na severidade de notificações E_STRICT
Todas as notificações E_STRICT foram reclassificadas para outros níveis.

# Mudanças na manipulação com a função list()
## Ordem
 
 ```
<?php
list($a[], $a[], $a[]) = [1, 2, 3];
var_dump($a);
?>
 ```

 **No PHP 5**

 ```
 array(3) {
  [0]=>
  int(3)
  [1]=>
  int(2)
  [2]=>
  int(1)
}
```

**No PHP 7**
```
array(3) {
  [0]=>
  int(1)
  [1]=>
  int(2)
  [2]=>
  int(3)
}
```

Um ponto interessante é uma recomendação da própria documentação

*"De modo geral, é recomendado não confiar na ordem em que as atribuições com que a função list() ocorrem, como sua implementação detalha, isso pode mudar novamente no futuro."*

## Atribuições Vazias
O código abaixo não é mais permitido
```
<?php
list() = $a;
list(,,) = $a;
list($x, list(), $y) = $a;
?>

```

# Foreach por valor opera em uma cópia do array
Quando usado no modo padrão, por valor, o foreach vai operar em uma cópia do array sendo iterado, ao invés do próprio array.

# Mudanças na manipulação do int
## Octais literais inválidos
Antes, octais literais que continham números inválidos, eram silenciosamente truncados (0128 se tornaria 012). Agora, um octal literal inválido causará um erro de parse. 

## Deslocamento de bits negativos
Agora será lançada uma exceção do tipo ArithmeticError
```
Fatal error: Uncaught ArithmeticError: Bit shift by negative number in /tmp/test.php:2
Stack trace:
#0 {main}
  thrown in /tmp/test.php on line 2
```

# Mudanças na manipulação de strings
## Strings hexadecimais não são mais consideradas numéricas
Strings contendo números hexadecimais não são mais consideradas numéricas. Por exemplo: 
```
<?php
var_dump("0x123" == "291");
var_dump(is_numeric("0x123"));
var_dump("0xe" + "0x1");
var_dump(substr("foo", "0x1"));
?>
```

**No PHP 5**
```
bool(true)
bool(true)
int(15)
string(2) "oo"
```

**No PHP 7**
```
bool(false)
bool(false)
int(0)

Notice: A non well formed numeric value encountered in /tmp/test.php on line 5
string(3) "foo"
```

# Novos objetos não podem ser atribuídos por referência
O código abaixo não é mais válido
```
<?php
class C {}
$c =& new C;
?>
```

# Nomes inválidos de classes, interfaces e traits
- bool
- int
- float
- string
- null
- true
- false

Os nomes abaixo **não** devem ser usados
- resource
- object
- mixed
- numeric

# Chamadas de contextos incompatíveis foram removidas
Anteriormente depreciadas no PHP 5.6, chamadas estáticas feitas a métodos não-estáticos com um contexto incompatível agora resultarão no método chamado tendo uma variável $this indefinida e um aviso de depreciação será emitido. 
```
<?php
class A {
    public function test() { var_dump($this); }
}

// Nota: NÃO extende A
class B {
    public function callNonStaticMethodOfA() { A::test(); }
}

(new B)->callNonStaticMethodOfA();
?>
```

**No PHP 5**
```
Deprecated: Non-static method A::test() should not be called statically, assuming $this from incompatible context in /tmp/test.php on line 8
object(B)#1 (0) {
}
```

**No PHP 7**
```
Deprecated: Non-static method A::test() should not be called statically in /tmp/test.php on line 8

Notice: Undefined variable: this in /tmp/test.php on line 3
NULL
```

# Funções não podem ter vários parâmetros com o mesmo nome
Não é mais possível definir dois ou mais parâmetros em uma função com o mesmo nome. O código abaixo irá disparar um E_COMPILE_ERROR
```
<?php
function foo($a, $b, $unused, $unused) {
    //
}
?>
```

# Declarações switch não podem ter vários blocos default
O código abaixo **não** é mais válido
```
<?php
switch (1) {
    default:
    break;
    default:
    break;
}
?>
```

# Comentários iniciados com # nos arquivos INI foram removidos 
Em vez de utilizar #, deve-se utilizar ;

# Ordenações de elementos iguais
O algoritmo interno de ordenação foi melhorado, o que pode resultar em diferentes ordenações de elementos, que são comparados como iguais, do que antes. 

De acordo com a documentação: *"Não confie na ordem de elementos que são comparados como iguais; ela pode mudar a qualquer momento."*

# Algumas Funções que foram removidas
1. Todas as funções ereg*
2. Sinônimos do mcrypt
3. Todas as funções ext/mysql e ext/mssql
4. Sinônimos de intl

---
# 7.0 - 7.1

# Throw ao passar poucos argumentos por parâmetro em funções
Anteriormente apenas um warning era emitido, agora este warning foi promovido para uma Error Exception
```
<?php
function test($param){}
test();
```
O código acima retornará o seguinte erro
```
Fatal error: Uncaught ArgumentCountError: Too few arguments to function test(), 0 passed in %s on line %d and exactly 1 expected in %s:%d
```

# Não é mais possível chamar dinâmicamente funções em escopo de introspecção
Chamadas dinâmicas para certas funções são proibidas na forma de $func(), por exemplo.
```
<?php
(function () {
    $func = 'func_num_args';
    $func();
})();

```

```
Warning: Cannot call func_num_args() dynamically in %s on line %d
```
 
 # Nomes inválidos de classes, interfaces e traits
 - void
 - iterable

 # DateTime constructor incorporates microseconds
 DateTime e DateTimeImmutable agora incorporam microsegundos quando construidos a partir do tempo atual ou por uma string relativa como *"first day of next mounth"*.

 # O operador de indice vazio não é mais suportado por strings mais
 Ao tentar aplicar o operador vazio de indices `[]` irá resultar em um fatal error em vez de converter silenciosamente para um array.

 # Diretivas ini removidas
 ```
 session.entropy_file
 session.entropy_length
 session.hash_function
 session.hash_bits_per_character
 ```
 
 # Ordem dos arrays foi modificada quando elementos são automáticamente criados durante atribuições por referência
 ```
<?php
$array = [];
$array["a"] =& $array["b"];
$array["b"] = 1;
var_dump($array);
?>
 ```

 **No Php 7.0**
 ```
array(2) {
  ["a"]=>
  &int(1)
  ["b"]=>
  &int(1)
}
```

**No PHP 7.1**
```
array(2) {
  ["b"]=>
  &int(1)
  ["a"]=>
  &int(1)
}
```

# JSON encoding e decoding
Agora a diretiva ini `serialize_precision`controla a precisão de serialização quando é realizado o encoding de floats

# ext/mcrypt foi depreciada
É recomendavél migrar para OpenSSL.

 ---
 # 7.1 - 7.2
 # number_format() não retorna mais um zero negativo
 ```
<?php

var_dump(number_format(-0.01)); // now outputs string(1) "0" instead of string(2) "-0"
 ```

# Warning ao tentar contar tipos não contáveis
Agora um warning será emitido.
```
<?php

var_dump(
    count(null), // NULL is not countable
    count(1), // integers are not countable
    count('abc'), // strings are not countable
    count(new stdclass), // objects not implementing the Countable interface are not countable
    count([1,2]) // arrays are countable
);
```

```
Warning: count(): Parameter must be an array or an object that implements Countable in %s on line %d

Warning: count(): Parameter must be an array or an object that implements Countable in %s on line %d

Warning: count(): Parameter must be an array or an object that implements Countable in %s on line %d

Warning: count(): Parameter must be an array or an object that implements Countable in %s on line %d
int(0)
int(1)
int(1)
int(1)
int(2)
```

# Constantes indefinidas geram um E_WARNING
Anteriormente era gerado um E_NOTICE e futuramente uma Error Exception.

---
# 7.2 - 7.3

# Warning ao usar continue em um switch
```
<?php
while ($foo) {
    switch ($bar) {
      case "baz":
         continue;
         // Warning: "continue" targeting switch is equivalent to
         //          "break". Did you mean to use "continue 2"?
   }
}
?>
```

# MySQL
Prepared Statements agora utilizam corretamente segundos fracionários, anteriormente eram apenas omitidos.

# SimpleXML
Operações matemáticas envolvendo objetos do SimplesXML agora tratam o texto como inteiro ou float caso for mais apropriado.
