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

// inserir no inicio: efeito de velocidade (Magia Haste / Barra carregou super rapido)
void inserirInicio(char* acao) {
    if (qtd >= MAX) return;
    // Empurra todas as acoes para a direita no vetor
    for (int i = qtd; i > 0; i--) {
        strcpy(deque[i], deque[i - 1]);
    }
    strcpy(deque[0], acao);
    qtd++;
}

// Remover no inicio: executa o ataque da vez
void removerInicio() {
    if (qtd == 0) return;
    printf("Batalha: Executando [%s]\n", deque[0]);
    // Puxa as acoes restantes para a esquerda
    for (int i = 0; i < qtd - 1; i++) {
        strcpy(deque[i], deque[i + 1]);
    }
    qtd--;
}

// Remover no fim: Jogador aperta 'B' e cancela(volta para o menude ação) a acao
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
    
    // Marle está sob efeito de Haste e sua barra enche instantaneamente
    printf("\nMarle esta com status Haste e sua barra de ATB enche mais rapido!\n");
    inserirInicio("Marle: Cura! "); // Devido a velocidade, assume a posicao 0
    exibir();
    
    printf("\n--- EXECUCAO DOS TURNOS ---\n");
    removerInicio(); // Executa a cura da Marle primeiro devido a sua velocidade
    removerFim();    // Jogador cancela a acao da Lucca apertando 'B'
    
    printf("\nEstado atual da batalha:\n");
    exibir();
    return 0;
}
