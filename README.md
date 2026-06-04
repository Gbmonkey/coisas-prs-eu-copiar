ATIVIDADE DE PESQUISA E IMPLEMENTACAO
Estruturas de Dados em Linguagem C
Instruções:
• Esta atividade é individual.
• Para cada estrutura, pesquise livremente, escolha um exemplo do cotidiano e
implemente em C.
• O código deve compilar e funcionar.
• Responda as questões com suas próprias palavras.

Parte 1 - Lista Linear
Uma lista linear é uma sequência de elementos onde cada um ocupa uma posição. Ela permite
buscar, inserir e remover elementos.

O que fazer? 
Pesquise como implementar uma lista linear em C. Escolha um contexto do seu cotidiano para o
exemplo, como uma lista de músicas, de contatos, de tarefas ou qualquer outro que preferir.
Implemente pelo menos as operações de busca, inserção e remoção.

Qual contexto você escolheu?
Descreva aqui o exemplo que você vai usar e o que cada operação significa nesse contexto:

Código implementado
Cole ou escreva seu código abaixo, ou anexe impresso:



Questões
a) Como funciona a operação de remoção na sua lista? O que acontece com os elementos
seguintes ao removido?
b) Qual é a diferença entre a lista com vetor e a lista com ponteiros (encadeada)? Qual você usou
e por que?

Parte 2 - Pilha (Stack)
A pilha segue a regra LIFO: o último elemento a entrar e o primeiro a sair. Toda inserção e
remoção acontece no topo.
O que fazer
Pesquise como implementar uma pilha em C. Escolha um contexto do seu cotidiano para o
exemplo, como um histórico de ações, uma pilha de pratos, livros empilhados ou qualquer outro.
Implemente as operações push, pop e exibir.
Qual contexto você escolheu?
Descreva aqui o exemplo que você vai usar e o que push e pop significam nesse contexto:
Código implementado
Cole ou escreva seu código abaixo, ou anexe impresso:
Questões
a) Se você fizer push de A, B e C nessa ordem e depois três pop, qual a ordem de saída? Por
que?
b) Dê um exemplo real, diferente do seu código, onde a regra LIFO faz sentido. Explique.

Parte 3 - Fila (Queue)
A fila segue a regra FIFO: o primeiro elemento a entrar e o primeiro a sair. Inserção acontece no
fim e remoção no início.
O que fazer
Pesquise como implementar uma fila em C. Escolha um contexto do seu cotidiano, como uma fila
de atendimento, de impressão, de mensagens ou qualquer outro. Implemente as operações
enqueue, dequeue e exibir.
Qual contexto você escolheu?
Descreva aqui o exemplo que você vai usar e o que enqueue e dequeue significam nesse
contexto:
Código implementado
Cole ou escreva seu código abaixo, ou anexe impresso:
Questões
a) Qual a diferença entre pilha e fila? Use seus próprios exemplos para explicar.
b) Se você implementou a fila com vetor, como evitou o problema da fila que 'anda' para a direita?
Se usou lista encadeada, qual a vantagem dessa escolha?

Parte 4 - Deque
O deque permite inserir e remover nos dois lados: tanto no início quanto no fim. É uma combinação
de pilha e fila.
O que fazer
Pesquise como implementar um deque em C. Escolha um contexto onde faz sentido operar pelos
dois lados, como um editor de texto com desfazer e refazer, uma fila de prioridade simples ou outro
exemplo de sua escolha. Implemente as operações de inserção e remoção nos dois lados.
Qual contexto você escolheu?
Descreva aqui o exemplo que você vai usar e o que cada operação significa:
Código implementado
Cole ou escreva seu código abaixo, ou anexe impresso:
Questões
a) Em que situação o deque e mais útil do que uma pilha ou uma fila simples? Explique com base
no seu exemplo.
b) O deque pode se comportar como pilha ou como fila. Como você faria isso usando apenas as
funções do seu deque?

Reflexão Final

Questão 1
Das quatro estruturas que você implementou, qual foi a mais difícil? O que gerou mais dúvida?
Questão 2
Qual é a principal diferença entre uma estrutura com vetor e uma com lista encadeada? Quando
vale a pena usar cada uma?
Questão 3
Imagine que você vai criar um aplicativo de verdade. Para cada situação abaixo, escreva qual
estrutura usaria e por que:
- Histórico de páginas visitadas num navegador (botão Voltar):
- Fila de espera num sistema de senhas:
- Lista de contatos de um celular:
- Sistema de desfazer e refazer ações num editor de texto:
