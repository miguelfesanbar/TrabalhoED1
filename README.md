# TrabalhoED1
Codigo para software da disciplina de Estrutura de Dados 1 
#include <stdio.h>
#include <stdlib.h>
#include <malloc.h>
#include <string.h>
#include <conio.h>
#include <locale.h>
#include <string.h>



typedef struct cuidador{
    char nomeCuidador[80];
    int cpfCuidador;
    char emailCuidador[40];
    int telefoneCuidador;


    }CUIDADOR;

typedef struct remedio
{
    char nomeRemedio[40];
    float dose;
    float horario;
    int codigo;

    struct remedio *prox;
} REMEDIO;

typedef struct paciente{
        char nomePaciente[80];
        int cpfPaciente;
        int dnasc;
        int telefonePaciente;
        char emailPaciente[50];
        CUIDADOR cuidador;


        struct paciente *prox;
    }PACIENTE;




    void inserir(PACIENTE **inicio, int escolhaCuidador){

        PACIENTE *novo;
        novo = (PACIENTE*)malloc(sizeof(PACIENTE));



        printf ("\n\nNome do paciente: ");
        scanf (" %[^\n]",&novo->nomePaciente);

        printf ("Cpf do Paciente: ");
        scanf (" %d",&novo->cpfPaciente);

        printf ("Telefone Paciente: ");
        scanf (" %d",&novo->telefonePaciente);

        printf ("Email do Paciente: ");
        scanf (" %[^\n]",&novo->emailPaciente);


        if(escolhaCuidador == 1){
            printf("\nNome do Cuidador: ");
            scanf (" %[^\n]",&novo->cuidador.nomeCuidador);

            printf("Digite o cpf do cuidador: ");
            scanf (" %d",&novo->cuidador.cpfCuidador);

            printf("Digite o telefone do cuidador: ");
            scanf (" %d",&novo->cuidador.telefoneCuidador);

            printf("Email do Cuidador: ");
            scanf (" %[^\n]",&novo->cuidador.emailCuidador);


        }

        if(*inicio == NULL){
            novo->prox = NULL;
            *inicio = novo;

        }else{
            novo->prox = *inicio;
            *inicio = novo;

        }


    }

    void inserirRemedio(REMEDIO **inicio, int cont){
        REMEDIO *novo;
        novo = (REMEDIO*)malloc(sizeof(REMEDIO));

        printf ("\n\nNome do remédio: ");
        scanf (" %[^\n]",&novo->nomeRemedio);

        printf ("\n\nInsira a dose do remédio: ");
        scanf (" %f",&novo->dose);

        printf ("Horário do remédio: ");
        scanf (" %f",&novo->horario);

        cont = novo->codigo; //Verificar se é com ou sem &

        if(*inicio == NULL){
            novo->prox = NULL;
            *inicio = novo;

        }else{
            novo->prox = *inicio;
            *inicio = novo;

        }


    }


    void consultar (PACIENTE *inicio)
    {
        PACIENTE *aux;
        aux = inicio;
        int procurado;

        printf ("Entre com o CPF que deseja alterar: ");
        scanf ("%d",&procurado);

        if (inicio==NULL)
        {
            printf ("Realize o cadastro primeiro!");
        }

        else
        {
            printf ("Pacientes cadastrados: \n");
            aux=inicio;
            while (aux!=NULL)
            {

                if (procurado==aux->cpfPaciente)
                {
                    printf (" ACHOU");

                }
            aux=aux->prox;

            }
        }
    }

    PACIENTE *editar (PACIENTE *inicio,int escolhaCuidador)
    {

        PACIENTE *aux;
        aux = inicio;
        int procurado=0, alterar=0, opcao=0;


        printf ("Entre com o CPF do paciente que deseja alterar: ");
        scanf ("%d",&procurado);
        printf("Digite 1 para alterar dados do paciente ou 2 para o do cuidador: ");
        scanf("%d", &alterar);

        if(alterar ==1){

            while (aux!=NULL)
            {

                if (procurado==aux->cpfPaciente)
                {
                    do{
                        printf("Escolha o que deseja alterar do cuidador: ");
                        printf ("/n/t");
                        printf ("1-Nome");
                        printf ("2-CPF");
                        printf ("3-Telefone");
                        printf ("4-Voltar para menu principal");
                        scanf ("%d",&opcao);

                        switch (opcao){
                            case 1:

                                printf("Digite o novo nome: ");
                                scanf(" %[^\n]", &aux->nomePaciente);
                                printf("Cpf alterado para: %s", aux->nomePaciente);

                            break;
                            case 2:
                                printf("Digite o novo cpf: ");
                                scanf(" %d", &aux->cuidador.cpfCuidador);
                                printf("Cpf alterado para: %d", aux->cpfPaciente);

                            break;
                            case 3:
                                printf("Digite o novo telefone: ");
                                scanf(" %d", &aux->telefonePaciente);
                                printf("Cpf alterado para: %d", aux->telefonePaciente);

                            break;

                            case 4:
                                main();
                            default:
                                printf ("Opção inválida");
                                main();
                        }
                    } while (opcao!=4);



                }
                aux=aux->prox;

            }

        }else if(alterar==2){

            while (aux!=NULL)
            {

                if (procurado==aux->cpfPaciente)
                {
                    do{
                        printf("Escolha o que deseja alterar do cuidador: ");
                        printf ("/n/t");
                        printf ("1-Nome");
                        printf ("2-CPF");
                        printf ("3-Telefone");
                        printf ("4-Voltar para menu principal");
                        scanf ("%d",&opcao);

                        switch (opcao){
                            case 1:

                                printf("Digite o novo nome: ");
                                scanf(" %[^\n]", &aux->cuidador.nomeCuidador);
                                printf("Cpf alterado para: %s", aux->cuidador.nomeCuidador);

                                break;
                            case 2:
                            printf("Digite o novo cpf: ");
                            scanf(" %d", &aux->cuidador.cpfCuidador);
                            printf("Cpf alterado para: %d", aux->cuidador.cpfCuidador);

                            break;
                        case 3:
                            printf("Digite o novo telefone: ");
                            scanf(" %d", &aux->cuidador.telefoneCuidador);
                            printf("Cpf alterado para: %d", aux->cuidador.telefoneCuidador);

                            break;

                        case 4:
                            main();
                        default:
                            printf ("Opção inválida");
                            main();
                        break;
                        }
                    } while (opcao!=4);



                }
                aux=aux->prox;

            }
        }



    return inicio;
    }

    REMEDIO *editarRemedio (REMEDIO *inicio)
    {
       REMEDIO *aux;
        aux = inicio;
        char nomeprocurado;
        int opcao=0;

        printf ("Entre com o CPF que deseja alterar: ");
        scanf (" %[^\n]",&nomeprocurado);

        while (aux!=NULL)
        {
            if (strcmp(aux->nomeRemedio, nomeprocurado) == 0){

            do
            {
                printf ("Escolha o dado que deseja alterar: ");
                printf ("1-Nome: ");
                printf ("2-Dose: ");
                printf ("3-Horário: ");
                printf ("4-Ir para menu principal");
                scanf ("%d",&opcao);

                switch (opcao)
                {
                case 1:
                    printf("Digite o novo nome do remedio: ");
                    scanf(" %[^\n]", &aux->nomeRemedio);
                    printf("Cpf alterado para: %s", aux->nomeRemedio);
                break;
                case 2:
                        printf("Digite a nova dosagem: ");
                        scanf(" %d", &aux->dose);
                        printf("Nova dose alterada para: %f", aux->dose);

                break;
                case 3:
                    printf("Digite o novo horário: ");
                    scanf(" %d", &aux->horario);
                    printf("Nova dose alterada para: %f", aux->horario);
                break;
                case 4:
                    main();
                default:
                    printf("Opção inválida!");
                    main();
                break;
                }

            }while (opcao!=4);

        }
    }
 }






    void imprimir(PACIENTE *inicio,  int escolhaCuidador){

        PACIENTE *aux;
        REMEDIO *aux1;
        aux = inicio;

        if(aux == NULL){
            printf("Paciente nao cadastrado! ");
        }else{
            do{
                printf("\n\nNome do paciente: %s \n", aux->nomePaciente);
                printf("Cpf do paciente: %d \n", aux->cpfPaciente);
                printf("Email do paciente: %s \n", aux->emailPaciente);
                printf("Telefone do paciente: %d \n\n", aux->telefonePaciente);
                //printf("%d \n", aux->dnasc);


                if(escolhaCuidador == 1){
                    printf("Nome do cuidador: %s \n", aux->cuidador.nomeCuidador);
                    printf("Cpf do cuidador: %d \n", aux->cuidador.cpfCuidador);
                    printf("Email do cuidador: %s \n", aux->cuidador.emailCuidador);
                    printf("Telefone do cuidador: %d \n\n", aux->cuidador.telefoneCuidador);
                }


                aux = aux->prox;
            }while(aux != NULL);
        }
    }




    main()
    {

        setlocale (LC_ALL,"Portuguese");
        int escolhaCuidador = 0;
        printf ("Existe cuidador? Sim(1), Nao (2): ");
        scanf ("%d",&escolhaCuidador);

        PACIENTE *inicio = NULL;
        int cont = 1;


        inserir(&inicio, escolhaCuidador);
        inserirRemedio(&inicio, cont);
        inicio = editar(inicio, escolhaCuidador);
        inicio = editarRemedio(inicio);
        imprimir(inicio, escolhaCuidador);


   }
