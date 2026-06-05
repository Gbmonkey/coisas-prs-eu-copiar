 
------------------------------
## Reflexão Final
Questão 1: Das quatro estruturas que você implementou, qual foi a mais difícil? O que gerou mais dúvida?

* R: O Deque foi a mais confusa e excruciante que eu fiz superando a número 1. A maior dúvida foi fazer a lógica no vetor para "empurrar" todos os elementos para a direita na hora de inserir no início, e "puxar" todo mundo para a esquerda na hora de remover do início, sem me. confundir totalmente alem de enquadra na ideia do chrono Trigger fiz no celular então foi bem difícil não perde a concentração ou ter medo de deleta tudo. 

Questão 2: Qual é a principal diferença entre uma estrutura com vetor e uma com lista encadeada? Quando vale a pena usar cada uma?

* R: A diferença principal é que o vetor tem tamanho fixo na memória e exige ficar arrastando os elementos para os lados nas alterações, enquanto a lista encadeada usa ponteiros, cresce dinamicamente e só muda os links de conexão. Vale a pena usar vetor quando sabemos o limite máximo de dados e queremos um código mais direto (como na Pilha de artbooks). Vale a pena usar lista encadeada quando o tamanho é totalmente imprevisível e muda muito (como na Playlist de músicas).

Questão 3: Imagine que você vai criar um aplicativo de verdade. Para cada situação abaixo, escreva qual estrutura usaria e por que:

* Histórico de páginas visitadas num navegador (botão Voltar):
* R: Pilha. Porque a última página que o usuário abriu precisa ser a primeira a reaparecer quando ele clicar em "Voltar" (regra LIFO).
* Fila de espera num sistema de senhas:
* R: Fila. Porque garante que o primeiro cliente a retirar a senha seja o primeiro a ser atendido no caixa, mantendo a ordem de chegada justa (regra FIFO).
* Lista de contatos de um celular:
* R: Lista Linear. Porque o usuário precisa buscar, inserir novos nomes ou deletar contatos específicos em qualquer posição da lista, sem ficar preso apenas às pontas.
* Sistema de desfazer e refazer ações num editor de texto:
* R: Deque. Porque permite empilhar as ações para desfazer em uma ponta e, se o histórico de ações ficar grande demais para a memória do aplicativo, podemos ir descartando as ações mais antigas pela outra ponta.

------------------------------
Com isso, o seu trabalho está 100% concluído e revisado! Todos os códigos compilam perfeitamente e as respostas fazem sentido entre si.
Quer que eu revise mais alguma linha específica antes de você salvar tudo para entregar, ou já está pronto para garantir o seu descanso hoje?

