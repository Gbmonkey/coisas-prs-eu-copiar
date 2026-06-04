#include <stdio.h>
#include <string.h>

#define MAX 5

// Vetor que guarda os nomes dos livros e o indicador do topo
char pilha[MAX][50];
int topo = -1; // Comeca em -1 porque a pilha está vazia

// Operacao PUSH: adiciona livro no topo
void push(char* livro) {
    if (topo >= MAX - 1) {
        printf("A pilha de livros esta cheia!\n");
        return;
    }
    topo++;
    strcpy(pilha[topo], livro);
}

// Operacao POP: remove livro do topo
void pop() {
    if (topo == -1) {
        printf("Nao ha livros na pilha!\n");
        return;
    }
    printf("Livro retirado do topo: %s\n", pilha[topo]);
    topo--;
}

// Operacao EXIBIR: mostra a pilha do topo para baixo
void exibir() {
    if (topo == -1) {
        printf("Pilha vazia.\n");
        return;
    }
    printf("\n--- PILHA DE LIVROS ---\n");
    for (int i = topo; i >= 0; i--) {
        printf("[ %s ]\n", pilha[i]);
    }
    printf("-----------------------\n");
}

int main() {
    // Colocando os livros na pilha
    push("Livro de Calculo");
    push("Livro de Fisica");
    push("Livro de C"); // Este fica no topo
    
    exibir();
    
    // Tirando o livro do topo
    pop();
    
    // Mostrando como ficou
    exibir();
    
    return 0;
}
