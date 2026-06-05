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
R=Uma playlist de música, usei minhas aristas favoritas.
Operações
Inserir: adiciona música no final da playlist; 
Buscar: procura uma música pelo nome;
Remover: remove uma música e libera a memória. 



Código implementado
Cole ou escreva seu código abaixo, ou anexe impresso:
#include <stdio.h> 
#include <stdlib.h> 
#include <string.h>

// Estrutura para cada musica da playlist
typedef struct Musica { 
    char nome[50]; 
    struct Musica* prox; 
} Musica;

// Funcao para colocar musica no fim da lista
void inserir(Musica** lista, char* nome) {
    Musica* novo = (Musica*)malloc(sizeof(Musica)); 
    strcpy(novo->nome, nome); 
    novo->prox = NULL;
    
    if (*lista == NULL) {
        *lista = novo;
    } else {
        Musica* atual = *lista;
        while (atual->prox != NULL) {
            atual = atual->prox;
        }
        atual->prox = novo;
    }
}

// procurar uma musica pelo nome
int buscar(Musica* lista, char* nome) { 
    while(lista != NULL) { 
        if (strcmp(lista->nome, nome) == 0) return 1; 
        lista = lista->prox; 
    } 
    return 0; 
}

// tirar uma musica da lista e liberar memoria
void remover(Musica** lista, char* nome) {
    Musica *atual = *lista, *ant = NULL; 
    while (atual != NULL && strcmp(atual->nome, nome) != 0) {
        ant = atual; 
        atual = atual->prox; 
    } 
    if (atual == NULL) return; 
    if (ant == NULL) *lista = atual->prox; 
    else ant->prox = atual->prox; 
    free(atual);
}

// mostrar a lista na tela
void exibir(Musica* lista) {
    int i = 1; 
    while (lista != NULL) { 
        printf("%d. %s\n", i++, lista->nome);
        lista = lista->prox;
    }
}

int main() { 
    Musica* minhaPlaylist = NULL;
    
    // Adicionando as musicas na playlist
    inserir(&minhaPlaylist, "Sofia - Clairo");
    inserir(&minhaPlaylist, "Motion Sickness - Phoebe Bridgers");
    inserir(&minhaPlaylist, "Bags - Clairo");
    
    printf("Playlist:\n");
    exibir(minhaPlaylist);
    
    // a busca
    if (buscar(minhaPlaylist, "Motion Sickness - Phoebe Bridgers")) {
        printf("\nMotion Sickness esta na playlist.\n");
    } else {
        printf("\nMotion Sickness nao encontrada.\n");
    }
    
    // a remocao
    remover(&minhaPlaylist, "Motion Sickness - Phoebe Bridgers");
    
    printf("\nDepois de remover Motion Sickness:\n");
    exibir(minhaPlaylist);
    
    return 0; 
}



Questões
a) Como funciona a operação de remoção na sua lista? O que acontece com os elementos
seguintes ao removido?
R: Ela escaneia a lista até encontrar o
nome, se encontrar, ela ajusta o ponteiro do nó anterior para ignorar o nó atual e depois libera a memória direto para o próximo. Os
elementos seguintes continuam na mesma ordem. 

b1) Qual é a diferença entre a lista com vetor e a lista com ponteiros (encadeada)? 
R: A diferença é que a lista com vetor tem um tamanho fixo e, quando apagamos algo no meio, precisamos "arrastar" todos os
elementos para preencher o buraco. Já a
lista com ponteiros cresce dinamicamente na memória e só precisa mudar a direção das conexões para remover ou inserir algo.
b2)Qual você usou e por que?
R: lista encadeada pois permite que a playlist cresça sem limite pré-definido


 2 - Pilha (Stack)
A pilha segue a regra LIFO: o último elemento a entrar e o primeiro a sair. Toda inserção e
remoção acontece no topo.

O que fazer
Pesquise como implementar uma pilha em C. Escolha um contexto do seu cotidiano para o
exemplo, como um histórico de ações, uma pilha de pratos, livros empilhados ou qualquer outro.
Implemente as operações push, pop e exibir.

Qual contexto você escolheu?
Descreva aqui o exemplo que você vai usar e o que push e pop significam nesse contexto:
R: Uma pilha de livro(tava pensando em uma coleção de artbook) 
Push: empilhaym livro novo no topo da pilha. 
Pop:  retirar o livro que esta no topo da pilha(último colocado) 
Exibir: mostra todos os livros na pilha, topo ate embaixo. 

Código implementado
Cole ou escreva seu código abaixo, ou anexe impresso:

#include <stdio.h>
#include <string.h>

#define MAX 5

char pilha[MAX][50]; // Vetor para guardar os nomes
int topo = -1;       // Comeca em -1 porque a pilha esta vazia

// PUSH: adiciona artbook no topo
void push(char* artbook) {
    if (topo >= MAX - 1) {
        printf("A pilha de artbooks esta cheia!\n");
        return;
    }
    topo++;
    strcpy(pilha[topo], artbook);
}

// POP: remove artbook do topo
void pop() {
    if (topo == -1) {
        printf("Nao ha artbooks na pilha!\n");
        return;
    }
    printf("Artbook retirado do topo: %s\n", pilha[topo]);
    topo--;
}

// EXIBIR: mostra a pilha do topo ate embaixo
void exibir() {
    if (topo == -1) {
        printf("Pilha vazia.\n");
        return;
    }
    printf("\n--- PILHA DE ARTBOOKS ---\n");
    for (int i = topo; i >= 0; i--) {
        printf("[ %s ]\n", pilha[i]);
    }
    printf("-------------------------\n");
}

int main() {
    // Colocando os artbooks na pilha
    push("One Piece Compendiums");
    push("Monster Hunter Illustrations");
    push("The Art of The Witcher 3"); // fica no topo da pilha
    
    exibir();
    
    // Tirando o livro do topo (The Art of The Witcher 3)
    pop();
    
    // como ficou a pilha na mesa
    exibir();
    
    return 0;
}


Questões
a1) Se você fizer push de A, B e C nessa ordem e depois três pop, qual a ordem de saída?
R: será C, B, A
a2) Por
que?
R: porque a
estrutura de pilha segue a regra do LIFO, como o C
foi o último empilhado,  logo ele foi o primeiro a sair. 

b) Dê um exemplo real, diferente do seu código, onde a regra LIFO faz sentido. Explique.
R: O ctrl+z no photoshop ou word usa una pilha. Cada ação e empilhada. Quando o usuário aperts essa tecla a última ação é removida primeira(LIFO), desfazendo na ordem inversa em Que foram feitas. 

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
Tela de um jogo MMO RPG que está tendo um dia cheio no server.
Enqueue: um novo jogador abriu o jogo e entrou na fila de espera no final
Dequeue: o primeiro player conseguiu  entrar para jogar e não esta mais na fila de espera. 

Código implementado
Cole ou escreva seu código abaixo, ou anexe impresso:

#include <stdio.h>
#include <string.h>

#define MAX 5

char fila[MAX][50]; // Vetor para guardar os nicks dos jogadores (matriz de strings)
int quantidade = 0; // Quantidade de pessoas na fila atual

// ENQUEUE: entra no fim da fila
void enqueue(char* nick) {
    if (quantidade >= MAX) {
        printf("Fila do servidor cheia!\n");
        return;
    }
    strcpy(fila[quantidade], nick);
    quantidade++;
}

// DEQUEUE: primeiro jogador entra no jogo e sai da fila
void dequeue() {
    if (quantidade == 0) {
        printf("Nenhum jogador na fila.\n");
        return;
    }
    printf("Jogador conectado ao servidor: %s\n", fila[0]);
    
    // Arrastando todo mundo para a esquerda (a fila anda)
    for (int i = 0; i < quantidade - 1; i++) {
        strcpy(fila[i], fila[i + 1]);
    }
    quantidade--;
}

// EXIBIR: mostra quem esta esperando
void exibir() {
    if (quantidade == 0) {
        printf("Fila vazia.\n");
        return;
    }
    printf("\n--- FILA DE ESPERA DO SERVIDOR ---\n");
    for (int i = 0; i < quantidade; i++) {
        printf("%d. %s\n", i + 1, fila[i]);
    }
    printf("------------------------------------\n");
}

int main() {
    // Jogadores tentando conectar
    enqueue("zecurica");
    enqueue("gyo");
    enqueue("Gbmoses");
    
    exibir();
    
    // Primeiro da fila entra no jogo (zecurica)
    dequeue();
    
    // Mostra como ficou a fila depois que andou
    exibir();
    
    return 0;
}


Questões
a) Qual a diferença entre pilha e fila? Use seus próprios exemplos para explicar.
R: está na regra de saída:
•Pilha: tira primeiro o último que entrou (LIFO). O meu de artbook onde se tira o de cima primeira. 
•Fila:tira o primeiro q entrou (FIFO). Essa fila de login e um exemplo, o primeiro jogador no queue entra no serve primeiro. 
b) Se você implementou a fila com vetor, como evitou o problema da fila que 'anda' para a direita?
Se usou lista encadeada, qual a vantagem dessa escolha?
Usei um Vetor simples. Quando p primeiro sai, eu movo todos os outros uma posição para a esquerda (forçando a fila a “andar para a esquerda ”) usando o for, a fila começa sempre pro vetor de posição 0.

Parte 4 - Deque
O deque permite inserir e remover nos dois lados: tanto no início quanto no fim. É uma combinação
de pilha e fila.

O que fazer
Pesquise como implementar um deque em C. Escolha um contexto onde faz sentido operar pelos
dois lados, como um editor de texto com desfazer e refazer, uma fila de prioridade simples ou outro
exemplo de sua escolha. Implemente as operações de inserção e remoção nos dois lados.

Qual contexto você escolheu?
Descreva aqui o exemplo que você vai usar e o que cada operação significa:
R: fila de comandos de batalha do chrono Tigger
Inserir fim: ataque normal carrega no. Tempo normal 
Inseri início: com haste (barra recarrega rápido) fura a fila
Remover início: executa o primeiro comando da fila 
Remover fim: o player apertar ‘B’
 E cancela a último comando escolhido

Código implementado
Cole ou escreva seu código abaixo, ou anexe impresso:

#include <stdio.h>
#include <string.h>

#define MAX 5
char deque[MAX][50]; // Vetor de strings para as ações de combate
int qtd = 0;

// Inserir no fim: comando de ataque normal (barra carregou normalmente)
void inserirFim(char* acao) {
    if (qtd >= MAX) return;
    strcpy(deque[qtd], acao);
    qtd++;
}

// inserir no inicio: efeito de velocidade (magia haste = barra carregou rapido)
void inserirInicio(char* acao) {
    if (qtd >= MAX) return;
    // Empurra todas as ações para a direita no vetor
    for (int i = qtd; i > 0; i--) {
        strcpy(deque[i], deque[i - 1]);
    }
    strcpy(deque[0], acao);
    qtd++;
}

// remover no inicio: executa o ataque da vez
void removerInicio() {
    if (qtd == 0) return;
    printf("Batalha: Executando [%s]\n", deque[0]);
    // puxa as ações restantes para a esquerda
    for (int i = 0; i < qtd - 1; i++) {
        strcpy(deque[i], deque[i + 1]);
    }
    qtd--;
}

// remover no fim: jogador aperta 'B' e cancela(volta para o menude ação) a ação
void removerFim() {
    if (qtd == 0) return;
    printf("Cancelado pelo jogador: [%s]\n", deque[qtd - 1]);
    qtd--;
}

void exibir() {
    if (qtd == 0) {
         printf("Nenhum comando na fila de batalha.\n");
         return;
    }
    printf("Fila de Turnos: ");
    for (int i = 0; i < qtd; i++) {
        printf("[%s] ", deque[i]);
    }
    printf("\n");
}

int main() {
    // Crono e Lucca escolhem ações (techs que custam pouco MP por exemplo) 
    inserirFim("Crono: Ciclone! ");
    inserirFim("Lucca: Lança-chamas! ");
    exibir();
    
    // Marle está sob efeito de Haste e sua barra enche rapidamente 
    printf("\nMarle esta com status Haste e sua barra de ATB enche mais rapido!\n");
    inserirInicio("Marle: Cura! "); // Devido a velocidade, assume a posicao 0
    exibir();
    
    printf("\n--- EXECUCAO DOS TURNOS ---\n");
    removerInicio(); // executa a cura da Marle primeiro devido a sua velocidade
    removerFim();    // jogador cancela a acao da Lucca apertando 'B'
    
    printf("\nEstado atual da batalha:\n");
    exibir();
    return 0;
}

ações uestões
a) Em que situação o deque e mais útil do que uma pilha ou uma fila simples? Explique com base
no seu exemplo.
R: quando e preciso mexer nas duas pontas. Comparado com o exemplo do jogo, uma fila simples não iria deixa a Marle fura a fila sob efeito de haste e pilha não iria funciona com a ordem de turnos, usando deque eu posso da prioridade a cura com haste e cancela a ação sem problemas. 
b) O deque pode se comportar como pilha ou como fila. Como você faria isso usando apenas as
funções do seu deque?
R: escolhendo duas das funções e ignorando as outras.
Para viras pilha(lifo): bastaria que o sistema usasse apenas as funções inserir Fin (para escolher ações) e remover fim (para cancelar as ações)
Para virar fila comum (FIFO): o jogo usaria apenas as funções inserir fim (conforme as barras de tempo normais terminam de carregar) e remover Inicio (para descarregar e executar cada golpe na tela).

Questão 1: Das quatro estruturas que você implementou, qual foi a mais difícil? O que gerou mais dúvida?R: Sem dúvida o Deque foi a mais difícil e chata de fazer. Ele superou até a lista linear. A parte que mais me deu dúvida foi a lógica de empurrar todos os elementos pra direita quando insere no início e puxar tudo pra esquerda quando remove do início. Quase me confundi inteiro várias vezes. Ainda tentei encaixar no tema de Chrono Trigger e fiz tudo no celular, então foi bem ruim pra manter a concentração e fiquei com medo de deletar alguma coisa errada.Questão 2: Qual é a principal diferença entre uma estrutura com vetor e uma com lista encadeada? Quando vale a pena usar cada uma?R: A diferença principal é que o vetor tem tamanho fixo e toda vez que você insere ou remove no meio tem que ficar arrastando os outros elementos. Já a lista encadeada cresce dinamicamente e só muda os ponteiros.  Vetor vale mais a pena quando você sabe o limite máximo de itens e quer algo mais simples (como a pilha de artbooks). Lista encadeada é melhor quando não se sabe quantos elementos vão ter e tem muitas inserções e remoções (como a playlist de músicas).Questão 3: Imagine que você vai criar um aplicativo de verdade. Para cada situação abaixo, escreva qual estrutura usaria e por que:Histórico de páginas visitadas num navegador (botão Voltar):
Usaria Pilha, porque a última página que você visitou tem que ser a primeira a voltar (LIFO).
Fila de espera num sistema de senhas:
Fila normal (FIFO), pra manter a ordem de chegada das pessoas.
Lista de contatos de um celular:
Lista Linear (encadeada). Porque a gente precisa buscar, adicionar ou remover contato em qualquer posição, sem ficar preso só nas pontas.
Sistema de desfazer e refazer ações num editor de texto:
Deque. Ele permite desfazer as ações de um lado e, se o histórico ficar muito grande, dá pra remover as ações mais antigas do outro lado.