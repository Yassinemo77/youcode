#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct livres{
    char titre[100];
    char auteur[100];
    int prix;
    int quantite;
};

int numBooks = 0;
int maxBooks = 100;

struct livres biblio[100];
void add(){
    if(numBooks > maxBooks){
        printf("la biblio is plein.");
    }
    printf("--------------------------------------------- \n");
    printf("entrer le nom de livres :");
    scanf("%s",&biblio[numBooks].titre);

    printf("entrer l'auteur de livres :");
    scanf("%s",&biblio[numBooks].auteur);

    printf("entrer le prix :");
    scanf("%d",&biblio[numBooks].prix);

    printf("entrer la quantite :");
    scanf("%d",&biblio[numBooks].quantite);

    numBooks++;
    printf("--------------------------------------------- \n");
}

void affichageLivres(){
    for(int i = 0 ;  i < numBooks ; i++){
        printf("===================================== \n");
        printf("livres num %d \n", i + 1);
        printf("   nom de livre est : %s \n" , biblio[i].titre);
        printf("   auteur de livre est : %s \n" , biblio[i].auteur);
        printf("   prix de livre est : %d \n" , biblio[i].prix);
        printf("   quantite de livre est : %d \n" , biblio[i].quantite);
        printf("--------------------------------------------- \n");
         printf("===================================== \n");
    }
}

void affichageMenu(){

    printf("1- ajouter un livre : \n");
    printf("2- afficher les livres : \n");
    printf("3- modifier un livre : \n");
    printf("4- supprimer un livre : \n");

}
void update(){
    char tab[100];
    printf("rechercher le livre pour la mise a jour : ");
    scanf("%s",&tab);
        if( numBooks > 0 ){
            for(int i = 0 ; i < numBooks ; i++){
                int res = strcmp(tab, biblio[i].titre);
                    if(res == 0 ){
                        printf("entrer la nouvelle valeur de quantite : ");
                        scanf("%d", &biblio[i].quantite);
                    }else{
                        printf("res is not found \n");
                    }
                }
        }
        else{
            printf("no books found /n");
            }
 }

void deletes(){
    char tab[100];
    printf("rechercher le livre pour delete : ");
    scanf("%s",&tab);
  for(int i = 0 ; i < numBooks ; i++){
    int res = strcmp(tab, biblio[i].titre);
        if(res == 0){
            printf("index of the book : %d \n", i);
            for(int j = i ; i < numBooks - 1 ; i++){
                biblio[j] = biblio[j + 1];
            }
         }else {
            printf("book not found");
        }
        }
}
int main()
{
    int choix;
    do{
printf("numBooks === %d \n",numBooks);
        affichageMenu();
        printf("entrer un choix : ");
        scanf("%d",&choix);
        switch(choix){
            case 1 :
                add();
                break;
            case 2 :
                affichageLivres();
                break;
            case 3 :
                update();
                break;
            case 4 :
                deletes();
                break;
        }
    }while(choix < 5);

    return 0;
}

