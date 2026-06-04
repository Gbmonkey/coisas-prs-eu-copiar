# coisas-prs-eu-copiar
Estácio 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct Musica {
    char nome[50];
    struct Musica* prox;
} Musica;

void inserir(Musica** lista, char* nome) {
    Musica* novo = (Musica*)malloc(sizeof(Musica));
    strcpy(novo->nome, nome);
    novo->prox = NULL;

    if (*lista == NULL) {
        *lista = novo;
    } else {
        Musica* atual = *lista;
        while (atual->prox != NULL) atual = atual->prox;
        atual->prox = novo;
    }
}

int buscar(Musica* lista, char* nome) {
    while (lista != NULL) {
        if (strcmp(lista->nome, nome) == 0) return 1;
        lista = lista->prox;
    }
    return 0;
}

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

int main() {
    Musica* minhaPlaylist = NULL;
    
    inserir(&minhaPlaylist, "Billie Jean");
    inserir(&minhaPlaylist, "Hotel California");
    
    int achou = buscar(minhaPlaylist, "Billie Jean");
    
    remover(&minhaPlaylist, "Billie Jean");
    
    return 0;
}
