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

// Funcao para procurar uma musica pelo nome
int buscar(Musica* lista, char* nome) { 
    while(lista != NULL) { 
        if (strcmp(lista->nome, nome) == 0) return 1; 
        lista = lista->prox; 
    } 
    return 0; 
}

// Funcao para tirar uma musica da lista e liberar memoria
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

// Funcao para mostrar a lista na tela
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
    
    // Testando a busca
    if (buscar(minhaPlaylist, "Motion Sickness - Phoebe Bridgers")) {
        printf("\nMotion Sickness esta na playlist.\n");
    } else {
        printf("\nMotion Sickness nao encontrada.\n");
    }
    
    // Testando a remocao
    remover(&minhaPlaylist, "Motion Sickness - Phoebe Bridgers");
    
    printf("\nDepois de remover Motion Sickness:\n");
    exibir(minhaPlaylist);
    
    return 0; 
}
