# CalculadoraIntegradoraESeno
algoritmo Calculadora_2funcoes;
// Síntese
//  Objetivo:  Calculadora de integral superior e inferior para melhor aproximação, e valores de seno
//  Entrada : subdivisões, fim e o inicio
//  Saída   :  média das integrais inferior e superior, caso o usuario queira, valores de seno


principal
	// Declarações
	real x, inicio, final;
	inteiro z, choose;
	inteiro p;
	// Instruções
	escreval("Escolha a função da calculadora");
	escreval ("Função 1 = Integral");
	escreval ("Função 2 = Seno");
	leia(choose);
	se (choose == 1) entao
		//Menu
		escreval(" ## ##     ##     ####      ## ##   ##  ###  ####       ##     ### ##    ## ##   ### ##     ##                ####   ###  ##  #### ##  ### ###   ## ##   ### ##     ##     ####");
		escreval("##   ##     ##     ##      ##   ##  ##   ##   ##         ##     ##  ##  ##   ##   ##  ##     ##                ##      ## ##  # ## ##   ##  ##  ##   ##   ##  ##     ##     ##");
		escreval("##        ## ##    ##      ##       ##   ##   ##       ## ##    ##  ##  ##   ##   ##  ##   ## ##               ##     # ## #    ##      ##      ##        ##  ##   ## ##    ##");
		escreval("##        ##  ##   ##      ##       ##   ##   ##       ##  ##   ##  ##  ##   ##   ## ##    ##  ##              ##     ## ##     ##      ## ##   ##  ###   ## ##    ##  ##   ##");
		escreval("##        ## ###   ##      ##       ##   ##   ##       ## ###   ##  ##  ##   ##   ## ##    ## ###              ##     ##  ##    ##      ##      ##   ##   ## ##    ## ###   ##");
		escreval("##   ##   ##  ##   ##  ##  ##   ##  ##   ##   ##  ##   ##  ##   ##  ##  ##   ##   ##  ##   ##  ##              ##     ##  ##    ##      ##  ##  ##   ##   ##  ##   ##  ##   ##  ##");
		escreval(" ## ##   ###  ##  ### ###   ## ##    ## ##   ### ###  ###  ##  ### ##    ## ##   #### ##  ###  ##             ####   ###  ##   ####    ### ###   ## ##   #### ##  ###  ##  ### ###");
		//Menu
		escreval(" Integrando para F(X) = 7x^4 + 2x^2 + x - 50");
		//Programa
		escreval("Insira o valor de subdivisoes, desejados: ");
		leia(p);

		escreval("Insira o inicio ");
		leia(inicio);

		escreval("Insira o  fim:");
		leia(final);
		escreval("Integral Inferior = ", integradorInferior(p, inicio, final));
		escreval("Integral Superior = ", integradorSuperior(p, inicio, final));
		escreval("Integral nos periodos desejados  = ", (integradorSuperior(p, inicio, final) + integradorInferior(p, inicio,final))/2);
		//Programa
	senao
		escreval("Escolha um valor multiplo de 10 ou 45 para consulta de seno");
		leia(z);
		seno(z);
	fimSe



fimPrincipal

funcao real integradorSuperior(inteiro x, real n, real T)
	inteiro i;
	real deltax, soma;
	deltax = (T-n)/x;
	soma = 0;
	para(i de 0 ate (x-1) passo 1)faca
		soma = soma + deltax*fdex(n + i*deltax);
	fimPara
	retorna soma;
fimFuncao

funcao real integradorInferior(inteiro x, real n, real T)
	inteiro i;
	real deltax, soma;
	deltax = (T-n)/x;
	soma = 0;
	para(i de 1 ate (x) passo 1)faca
		soma = soma + deltax*fdex(n + i*deltax);
	fimPara
	retorna soma;
fimFuncao

funcao real fdex(real x)
	retorna 7*x*x*x*x + 2*x*x + x - 50;
fimFuncao

funcao real seno(inteiro grau)
	real vetor[91], select;
	se(grau%10 != 0 e grau != 45 ou grau < 91 e grau > -1)entao
		vetor[0] = 0;
		vetor[10] = 0.1736;
		vetor[20] = 0.342;
		vetor[30] = 0.5; //30
		vetor[40] = 0.6428;
		vetor[45] = 0.7071; //45
		vetor[50] = 0.766;
		vetor[60] = 0.866; //60
		vetor[70] = 0.9397;
		vetor[80] = 0.9848;
		vetor[90] = 1;
		select = vetor[grau];
		escreval("");
		escreva("o seno de ");
		escreva(grau);
		escreva(" é igual a ");
		escreva(select);
	senao
		escreval("valor nao permitido!");
	fimSe
	retorna 0;
fimFuncao
