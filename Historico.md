# Histórico
### Abaixo um breve histórico das versões do PHP (estudo aprofundado da linguagem)
Foquei nas versões em si, as .x são para correção de bugs e problemas de segurança, mas cada versão abaixo teve diversas .x justamente para essas correções, por ser um software está sujeito a erros e bugs.
---

PHP 3.0: Primeira versão que se assemelha ao PHP atual, além da mudança de nome para PHP, um ponto forte é a extensibilidade que provê para os usuários uma interface para multiplas base de dados, protocolos e APIs.

PHP 4.0: Reescrita completa do core da linguagem, nova engine a zend engine, suporte para mais webservers, HTTP Sessions, buffering, manuseio de inputs do usuário e diversos novos construtores da linguagem.

PHP 4.1: Nova interface de usuário para melhorar a segurança, performance altamente aprimorada em especial em ambientes Windows, Suporte para versionar extensões, entre muitas outras funções e otimizações.

PHP 4.2: Variáveis externas não são mais registradas como variáveis globais e perfomance altamente aprimorada no upload de arquivos.

PHP 4.3: GD é empacotada pela distribuição, melhorias de performnance numa variedade de funções relativas a string, atualização de lib padrão melhorando a segurança, entre outras melhorias.

PHP 4.4: Lançamento de correção de bugs de corrupção de memória ao utilizar referencias, resolução de problemas de segurança do shtool.

PHP 5.0: Reescrita do suporte a XML, inclusão do mysqli com suporte para as novidades do mysql da época como PREPARED STATEMENTS

PHP 5.1: Reescrita do manuseio de data com suporte a timezone aprimorado, melhoria de perfomance comparado ao 5.0.x, PDO HABILITADA POR PADRÃO, 30 novas funções e diversas extensoes, PCRE e SQLite atualizados para ultimas versões (da época), 400 correções de bugs, PEAR atualizado para 1.4.5

PHP 5.2: Novo gerenciador de memória para a zend engine, input e json extensions foram adicionadas e habilitadas por padrão, introduzida extensão zip, hooks para trakear upload de arquivos, ADICIONADO DATETIME e DATETIMEZONE, atualizados SqLite e PCRE, OpenSSL MMysql e postgreesql para windows atualizados, melhorias de performance e correção de 200 bugs.

PHP 5.3: SUPORTE PARA NAMESPACES, funções lambda e CLOSURES, TERNÁRIOS, melhorias no arredondamento de floats, deprecations são capturados via E_DEPRECATED, mais flexibilidade no php.ini, nosas extensões phar intl fileinfo sqlite3 enchante, mais de 140 bugs corrigos e otimizações

PHP 5.4: Removido funções legadas, adicionado suporte para short array, ADICIONADO SUPORTE PARA TRAITS, E-ALL agora inclui E_STRICT, aprimorado engine zend para uso de memória, e muitas outras melhorias e otimizações no core.

PHP 5.5: Adicionado generators e coroutines, adicionado finally, adicionado plataforma simplificada de hash para senhas, resolução de nome de classe escavavel via ::class, atualização da lib gb, melhorias de performance e otimizações.

PHP 5.6: Expressoes escalaveis constantes, exponencialização usando `**`, FUNÇÕES E CONSTANTES PODEM SER IMPORTADAS USANDO A PALAVRA USE, uploads de arquivos maiories que 2GB são suportados, melhorias e correções de bugs.

PHP 7.0: Melhorias na perfomance sendo até 2x mais rapido que o 5.6, diminuição no consumo de memoria, árvore abstrata de sintaxe, suporte consistente à 64 bits, melhorias na hieraquia de excessões, MAIORIA DOS FATAL ERROS CONVERTIDOS PARA EXCEPTIONS, geração segura de números aleatórios, removido suporte antigo a SAPIs, NULL COALECING OPERATOR, CLASSES ANÔNIMAS.

PHP 7.1: Nullable types, VOID PARA RETORNO, modificadores de visibilidade para classes constantes, melhorias e correções de bugs.

PHP 7.2: Suporte para conversão de chaves numericas em cast de objetos/arrays, um warning é emitido ao tentar contar algo não contável, NOVO TIPO OBJETO, ARGON2 NO PASSWORD HASH, mcrypt removido, nova extensão sodium.

PHP 7.3: Aprimorado log FPM, Aprimorado deleção de arquivos em windows, diversas deprecações em funções.

PHP 7.4: PROPRIEDADES TIPADAS, ARROW FUNCTIONS, Limitar o tipo de retorno e o tipo de argumento, desempacotamento dentro de arrays, referências fracas, suporte para exceptions vindo de `__toString`, diversas deprecations e extensões removidas do core.

PHP 8.0: Argumentos nomeados, Union Types, MATH EXPRESSION, NULLSAFE OPERATOR, JIP compilation, muitas outras melhorias de sintaxe, correções de bugs.

PHP 8.1: Enumerações, PROPRIEDADES SOMENTE LEITURA, never return type,novas funções fsync fdatasync array_is_list, muitas outras melhorias , correções de bugs.




