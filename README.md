#include <stdio.h>
#include <string.h>

#define MAX 5

char fila[MAX][50]; // Vetor para guardar os nicks dos jogadores (matriz de strings)
int quantidade = 0; // Quantidade de pessoas na fila atual

// ENQUEUE: jogador entra no fim da fila
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
