# Questionário Sistemas Embarcados I

João Eduardo Moya - 11921EAU010

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.
- Quando um programa tem sua compilação feita em um sistema operacional ou plataforma diferente da qual é executado temos a chamada compilação cruzada. Sendo assim, serve para o desenvolvimento de softwares para plataformas diferentes da que o desenvolvedor está utilizando.
## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?
- O startup é o ponto de partida crítico para o sistema operacional, ou seja, antes do main. As suas principais funções são: iniciar as variáveis globais, configurar a memória e o processador e preparar para executar o código principal do programa.
## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.
- Makefile é o arquivo que possui um conjunto de instruções necessárias para o utilitário Make ser capaz de fazer a compilação de arquivos, programas e bibliotecas automática. Nele contém comandos que devem ser utilizados e como lidar com erros. Os elementos do makefile são: regras explícitas, implicitas, definição de variáveis, diretivas e comentários.
#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.
-O make analisa todo o código que foi descrito no Makefile e também compila os arquivos-fonte necessários para criação de um arquivo objeto executável.
#### (c) Qual é a sintaxe utilizada para criar um novo **target**?
targets:prerequisites
recipe
#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?
-As dependências do target são definidas depois da sua declaração. São usadas para garantir que um arquivo que tem dependências seja atualizado de acordo com as suas depedências. Quando a dependência é atualizada, o target deve ser recompilado e o make saberá disso na próxima execução.
#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
As chamadas regras do makefile são intruções que são responsáveis pela definição de criar um arquivo destino apartir de uma dependência. Regras explícitas tem a função de dar ao make quais são os arquivos que dependem de outros arquivos. E as regras implicitas informam ao make quais são os comandos que devem ser executados para a compilação do programa em geral.
## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?
O conjunto de instruções Thumb pode ser definido como sendo um subconjunto de instruções ARM, assim comprime 32 bits para 16 bits reduzindo a quantidade de memória gerada pelo código e o tamanho do Hardware. Sendo assim, a Thumb tem uma instrução ARM equivalente, embora o contrário são seje possível e consegue alternar entre os dois tipos de instrução Thumb e ARM do processador. E também, ele atualiza sempre as flags de condição.
### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Register***.
-Na arquitetura ARM Load/Store, todas as operações aritméticas e lógicas ocorrem entre registradores em primeiro lugar, antes que esses dados sejam transferidos para a memória. Em outras palavras, somente instruções de carregamento (load - leitura) e armazenamento (store - escrita) têm permissão para interagir diretamente com a memória. Por outro lado, na arquitetura Register/Register, todas as operações são realizadas exclusivamente entre registradores da CPU, dispensando qualquer acesso à memória. Esse método torna essa arquitetura mais eficaz, especialmente em termos de desempenho e em situações que envolvem manipulação intensiva de dados.
### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.
Os níveis de acesso de execução de código em processadores ARM Cortex-M referem-se à autorização para acessar diferentes regiões de memória onde o código é executado. Esses níveis são cruciais para garantir a segurança, a integridade e a eficiência do sistema. Existem principalmente dois tipos de níveis de acesso de execução de código em sistemas Cortex-M:
Execute-in-Place (XiP):
-Nesse modo, o código é executado diretamente da memória onde está armazenado, geralmente a memória de programa (flash).
-O processador busca as instruções diretamente da memória, sem a necessidade de carregá-las em outra área.
-A memória de programa é tipicamente apenas leitura (ROM), o que impede modificações no código durante a execução.
-Esse modo é comum em sistemas embarcados, onde a memória flash armazena o código do programa.
Execute-in-Place (DiP):
-Nesse modo, o código é copiado da memória de programa para a memória de dados (RAM) antes da execução.
-Isso pode ser necessário quando a memória de programa é mais lenta para execução direta ou quando há restrições de segurança.
-O código é temporariamente carregado na memória de dados apenas para a execução e pode ser descartado após o término.
O funcionamento do processador Cortex-M depende do tipo de acesso de execução de código definido para a região de memória onde o código está armazenado. No modo XiP, as instruções são buscadas diretamente da memória de programa. No modo DiP, as instruções são copiadas da memória de programa para a memória de dados antes da execução. A escolha entre XiP e DiP deve considerar as necessidades específicas do sistema, como velocidade de execução, consumo de energia e requisitos de segurança .
### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.
As interrupções são gerenciadas pelo sistema de prioridades em níveis de exceção e grupos de prioridade. Existem vários tipos de interrupções, como reset, IRQ, FIQ e SVC, cada um com sua própria prioridade. Para organizar melhor as interrupções, elas são agrupadas em níveis de prioridade. Dentro desses grupos, são criadas prioridades adicionais. O grupo é chamado de “Group Priority” (prioridade do grupo) e as propriedades adicionais são denominadas “Sub-Priority” (subprioridade). Essa estrutura permite que o sistema lide eficientemente com as interrupções, garantindo que as mais importantes sejam tratadas primeiro.
### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?
-O CPSR (ou PSR) é um registro que mantém o estado atual do processador. Ele registra informações importantes, como o modo de operação atual (usuário, supervisor, etc.), as condições de flags (como o flag de overflow), e outras configurações relevantes.
Por outro lado, o SPSR (ou PSR) é usado para armazenar temporariamente o estado do processador durante exceções e interrupções. Quando uma exceção ocorre (por exemplo, uma interrupção de hardware), o processador salva seu estado atual no SPSR antes de lidar com a exceção. Isso permite que o processador retome a execução normal após a exceção sem perder informações críticas.
Portanto em resumo, o CPSR mantém o estado geral do processador, enquanto o SPSR é usado para preservar temporariamente o estado durante exceções. 
### (f) Qual a finalidade do **LR** (***Link Register***)?
-O Link Register armazena o endereço de retorno de uma sub-rotina. Quando ocorre uma interrupção, o Link Register guarda o endereço de retorno. Dessa forma, após o tratamento da interrupção, o programa pode retomar a execução a partir desse ponto específico indicado pelo endereço de retorno. 
### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?
-O Program Status Register (PSR) tem como objetivo armazenar informações sobre o estado atual do processador. Ele desempenha um papel crucial no controle do fluxo de execução do programa e na eficaz gestão de exceções. 
### (h) O que é a tabela de vetores de interrupção?
-É uma tabela de endereços de memória que associa uma lista de manipuladores de interrupção a uma lista de solicitações de interrupção. Cada vetor de interrupção contém o endereço de um tratador de interrupção específico. Se uma interrupção é gerada, o processador salva seu estado atual e começa a executar o tratamento de interrupção apontado pelo vetor garantindo que nenhuma das tarefas executadas tenha conflito.
### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?
-O Nested Vectored Interrupt Controller (NVIC) administra as interrupções de forma hierárquica, considerando a prioridade e a eficiência. Assim, possibilitando que as interrupções tenham prioridade em função da sua importância. Além disso, o NVIC suporta o conceito de interrupção aninhada, o que significa que uma interrupção pode ocorrer enquanto outra está sendo tratada. Isso permite que algumas interrupções sejam temporariamente desativadas.
### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 
Se ocorre uma exceção por exemplo uma interrupção no  Cortex-M, Link Register faz o retorno dessa exceção. Diferente da função convencional em que o LR armazena o endereço de retorno, durante uma interrupção, o LR recebe um valor especial chamado EXC_RETURN

O EXC_RETURN contém informações essenciais sobre o contexto da pilha, o estado da exceção e outros detalhes relevantes para garantir um retorno adequado. Seus diferentes bits indicam aspectos fundamentais, como:

1-Se a pilha foi ajustada automaticamente durante o tratamento da exceção.
2-Se o retorno deve ser realizado para o modo Handler ou Thread.
3-Se uma pilha diferente deve ser utilizada no retorno.
4-Se o processador deve voltar ao modo Thumb ou ARM.

Ao retornar de uma interrupção, o processador utiliza a instrução BX LR interpretando o valor armazenado no registrador LR (EXC_RETURN). Nos bits de maior importância, o processador faz a execução das ações , como ajustar a pilha. Esse mecanismo permite que o Cortex faça interrupção efetiva, se adaptando  ao contexto da exceção ocorreu.
### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 
A diferença entre os processadores Cortex-M3 e Cortex-M4F está relacionada ao suporte de ponto flutuante, o impacto no tempo de resposta e no uso da pilha.

No Cortex-M3, quando ocorre uma interrupção é automaticamente salvo na pilha principal. Porém, no Cortex-M4F, que possui suporte a ponto flutuante, é pode-se usar uma pilha de contexto separada para os registradores durante uma interrupção. Permitindo uma maior flexibilidade no gerenciamento dos registradores.

O Lazy Stack é uma técnica de otimização de tempo e espaço na pilha para que sejam tratadas as interrupções. Em vez de alocar uma pilha fixa para cada thread, a pilha lazy é alocada dinamicamente apenas quando necessário. Essa abordagem economiza tempo e espaço na pilha para o tratamento de interrupções. Assim, possibilita adiar o salvamento dos registradores de ponto flutuante até que eles sejam efetivamente usados em uma interrupção. A configuração do Lazy Stack é realizada por meio do LSPACT e pode ser utilizada para ativa-la ou desativa-la





