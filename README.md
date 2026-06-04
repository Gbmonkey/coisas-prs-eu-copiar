
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
R: o botão “Voltar ” no navegador de internet, no navegador como firefox cada vez que visitamos uma página ela empilha. Se eu entro num site A depois B e C e se você aperta o botão de voltar, o sistema remove e te joga
exatamente para a última página que
você tinha visitado antes da atual, 
em sequência.
