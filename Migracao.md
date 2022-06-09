# Migrações de versões do PHP
### 5.6 para 7.0
#### Novas Features do PHP 7.0 que impactam na migração

1. PHP 7 teve seu core reconstruido, melhorando em até 9x a velocidade.

2. Com o PHP 7 os erros serão excessões e não erros fatais, podendo assim tratar a excessão e continuar a interpretação do código sem interrompe-lo.

3. Novos operadores, spaceship e null coalescing (que verifica se uma variável existe sem a necessidade do isset).

4. Suporte a indução de tipos, é possivel criar variaveis dos tipos, int, float, string e bool e usa-los para indicar qual tipo de valor uma função retornará.

5. Suporte a classes anônimas.

6. Suporte ao unicode.

7. Retirada de funções como mysql_ (sendo englobadas na mysqli_) e ereg_ (englobadas na lib PCRE com prefixo preg_.
