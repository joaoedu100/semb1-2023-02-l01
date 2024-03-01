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

### (f) Qual a finalidade do **LR** (***Link Register***)?

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?

### (h) O que é a tabela de vetores de interrupção?

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 


## Referências

### Básicas

[1] [STM32F411xC Datasheet](https://www.st.com/resource/en/datasheet/stm32f411ce.pdf)

[2] [RM0383 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0383-stm32f411xce-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

[3] [Using the GNU Compiler Collection (GCC)](https://gcc.gnu.org/onlinedocs/gcc/index.html)

[4] [GNU Make](https://www.gnu.org/software/make/manual/html_node/index.html)

### Vídeos Microsoft Teams

[5] [05 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[6] [06 - Arquitetura Cortex-M Parte 1/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[7] [07 - Arquitetura Cortex-M Parte 2/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[8] [08 - Microcontroladores STM32](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[9] [10 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

### Material Suplementar

[5] [A General Overview of What Happens Before main()](https://embeddedartistry.com/blog/2019/04/08/a-general-overview-of-what-happens-before-main/)
 
[6] [Bare metal embedded lecture-1: Build process](https://youtu.be/qWqlkCLmZoE?si=mn5yDnJYudQ1PpZH)
 
[7] [Bare metal embedded lecture-2: Makefile and analyzing relocatable obj file](https://youtu.be/Bsq6P1B8JqI?si=yuNLPj3JQ-2IT1yo)
 
[8] [Bare metal embedded lecture-3: Writing MCU startup file from scratch](https://youtu.be/2Hm8eEHsgls?si=c27MpZ47ApiMSwHR)
 
[9] [Lecture 15: Booting Process](https://youtu.be/3brOzLJmeek?si=MsHRUEJP8zofjwJQ)
