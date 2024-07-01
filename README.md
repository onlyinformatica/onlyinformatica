#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define nome "dati.txt"
#define uscita "dati.txt"
typedef struct informazioni {

	int numero;
	char parola[32];

}info;

typedef struct nodo {

	 info  dati;
	 struct nodo* succ;

}tnodo,*pnodo;



int menu() {

	int scelta;

	printf("\n\n*** M E N U ***\n"
		"quesito 1.\n"
		"quesito 2.\n"
		"quesito 3.\n"
		"quesito 4.\n"
		"quesito 5.\n"
		"quesito 6.\n"
		"quesito 7.\n"

	);
	printf("\n scegli -> ");
	scanf("%d", &scelta);

	return scelta;
}

pnodo creanodo(pnodo testa, info aux) {


	pnodo nuovo = (pnodo)malloc(sizeof(tnodo));
	if (nuovo == NULL)return testa;
	nuovo->dati = aux;
	nuovo->succ = testa;
	testa = nuovo;
	return testa;


}

pnodo carica(pnodo testa) {

	info aux;

	FILE* f = fopen(nome, "r");
	if (f == NULL) {
		printf("\nerrore nell'apertura del file\n");
		return NULL;
	}
	while (!feof(f)) {

		if (fscanf(f, "", ) == ) {



		}

testa=creanodo(testa, aux);

	}

	fclose(f);
	return testa;
}

void quesito2() {


}

void quesito3() {


}

void quesito4() {


}
void quesito5() {


}

void quesito6() {


}
void quesito7() {


}

void salva(pnodo testa) {

	FILE* f = fopen(uscita, "w");
	if (f == NULL) {
		printf("\nerrore nell' apertura file\n");
		return;
	}

	while (testa != NULL) {

		fprintf(f, "", );

		testa = testa->succ;
	}


	fclose(f);
}

void disalloca(pnodo testa) {

	pnodo p;
	while (testa != NULL) {
	p=testa;
		testa = testa->succ;
		free(p);
	}

}

int main() {
	pnodo testa = NULL;
	int scelta;
	
	do {
		scelta = menu();
		switch (scelta) {

		case 1:
			testa = carica(testa);
			break;
		case 2:
			quesito2();
			break;
		case 3:
			quesito3();
			break;
		case 4:
			quesito4();
			break;
		case 5:
			quesito5();
			break;
		case 6:
			quesito6();
			break;
		case 7:
			quesito7();
			break;


		default:
			break;

		}

	} while (scelta != 0);


	salva(testa);
	disalloca(testa);
	return 0;
}
