# Novidades do PHP
**Atenção:** Abaixo estão listadas as novidades que mais chamaram a minha atenção ou que mais irão impactar meu dia a dia profissional e acadêmico.

### 5.6 para 7.0
#### Novas Features do PHP 7.0

1. PHP 7 teve seu core reconstruido, melhorando em até 9x a velocidade.

2. Com o PHP 7 os erros serão excessões e não erros fatais, podendo assim tratar a excessão e continuar a interpretação do código sem interrompe-lo.

3. Novos operadores, spaceship e null coalescing (que verifica se uma variável existe sem a necessidade do isset).

4. Suporte a indução de tipos, é possivel criar variaveis dos tipos, int, float, string e bool e usa-los para indicar qual tipo de valor uma função retornará.

5. Suporte a classes anônimas.

6. Suporte ao unicode.

7. Retirada de funções como mysql_ (sendo englobadas na mysqli_) e ereg_ (englobadas na lib PCRE com prefixo preg_.

---

### 7.0 para 7.1
#### Novas Features do PHP 7.1
1. Nullable Types
    Declarações de tipo para parâmetros e valores de retorno agora podem ser marcados como nullable adicionado uma ? antes do tipo, sendo assim, isso significa que pode ser passado null para um argumento ou ainda que pode ser retornado um valor ou null.

    ```
    <?php

    function testReturn(): ?string
    {
        return 'elePHPant';
    }

    var_dump(testReturn());

    function testReturn(): ?string
    {
        return null;
    }

    var_dump(testReturn());

    function test(?string $name)
    {
        var_dump($name);
    }

    test('elePHPant');
    test(null);
    test();

    ```

    O retorno será

    ```
    string(10) "elePHPant"
    NULL
    string(10) "elePHPant"
    NULL
    Uncaught Error: Too few arguments to function test(), 0 passed in...
    ```
2. Funções void
    O tipo de retorno void foi introduzido, sendo assim funções que utilizem este tipo como sendo o seu tipo de retorno devem omitir o return statement ou utilizar um return vazio. **NULL não é válido neste caso**

    ```
    function f1(): void {}
    ```

3. Visibilidade de constantes de classe
    Agora as constantes de classe possuem suporte para visibilidade

    ```
    <?php
    class ConstDemo
    {
        const PUBLIC_CONST_A = 1;
        public const PUBLIC_CONST_B = 2;
        protected const PROTECTED_CONST = 3;
        private const PRIVATE_CONST = 4;
    }
    ```

4. Manuseio de multiplas exceptions em um catch
    Em casos onde é possível ocorrer diferentes exceptions.

    ```
    <?php
    try {
        // some code
    } catch (FirstException | SecondException $e) {
        // handle first and second exceptions
    }
    ```

5. Conversão de callables para Closures com Closure::fromCallable()
    ```
    <?php
    class Test
    {
        public function exposeFunction()
        {
            return Closure::fromCallable([$this, 'privateFunction']);
        }

        private function privateFunction($param)
        {
            var_dump($param);
        }
    }

    $privFunc = (new Test)->exposeFunction();
    $privFunc('some value');
    ```
6. Diversas melhorias à extensão Curl, dentre elas, suporte a HTTP/2 Server Push. 

7. Incrementos na utilização list()
