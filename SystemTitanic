#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <locale.h>

//Parâmetros de chamada de função.
void verifica_idade_struct();
void verifica_sexo_e_situacao_txt();
void verifica_sexo_e_situacao_struct();
void verifica_classe_txt();
void verifica_classe_struct();
void mostrar_faixa_etaria_e_sexo();
int valida_arquivo(char *nome_arquivo);
char verifica_usuario();
void cadastro_sistema();
int entrar_sistema();
void verifica_faixa_etaria_struct();
void verifica_faixa_etaria_txt();
void limpar_arquivos();
void median(int *arr, int n);
void ordenar(int *arr, int n);
void porcentagem_vivos();
void remove_arquivos();
void exibe_sexo();
void exibe_classe();
void exibe_situacao();
void exibe_estatistica();
void menu_principal();

//Struct com vetor com os dados dos passageiros.
struct{
  int classe;// 1, 2, 3, 4=Tripulacao
  int situacao; // 0-MORTO ou 1- VIVO
  int sexo; // 0-MASCULINO, 1-FEMININO
  int idade;
  int faixa_etaria; // 0-Criança, 1-Adulto
}psg[2201];

//Atribuições de operadores de manipulação de arquivos.
char leitura[5] = "r";
char escrita[5] = "w";
char abrir[5] = "a";

//Atribuição do arquivo passageiros.txt e todos arquivos auxiliares utilizados.
char passageiros[50] = "passageiros.txt";

char admin[50] = "admin.txt";

char lista_adultos[50] = "adultos.txt";
char lista_criancas[50] = "criancas.txt";

char lista_femininos[50] = "femininos.txt";
char lista_masculinos[50] = "masculinos.txt";

char lista_sobreviventes_adultos[50] = "sobreviventes_adultos.txt";
char lista_nsobreviventes_adultos[50] = "nsobreviventes_adultos.txt";

char lista_sobreviventes_criancas[50] = "sobreviventes_criancas.txt";
char lista_nsobreviventes_criancas[50] = "nsobreviventes_criancas.txt";

char lista_sobreviventes_femininos[50] = "sobreviventes_femininos.txt";
char lista_nsobreviventes_femininos[50] = "nsobreviventes_femininos.txt";

char lista_sobreviventes_masculinos[50] = "sobreviventes_masculinos.txt";
char lista_nsobreviventes_masculinos[50] = "nsobreviventes_masculinos.txt";

char lista_passageiros_1st[50] = "passageiros_1st.txt";
char lista_passageiros_2nd[50] = "passageiros_2nd.txt";
char lista_passageiros_3rd[50] = "passageiros_3rd.txt";
char lista_passageiros_tripulacao[50] = "passageiros_tripulacao.txt";

/*O bloco do main foi usado para o preenchimento dos arquivos auxiliares e a chamada do menu.*/
int main(){
  setlocale(LC_ALL, "Portuguese");          //Permissão dos elementos em da Língua Portuguesa.

  limpar_arquivos();                        //As ações e responsabilidade das funções seram revisadas a seguir.

  //preencher o struct global
  verifica_idade_struct();
  verifica_classe_struct();
  verifica_faixa_etaria_struct();
  verifica_sexo_e_situacao_struct();
  verifica_faixa_etaria_struct();

  //preencher os txts...
  verifica_sexo_e_situacao_txt();
  verifica_classe_txt();
  verifica_faixa_etaria_txt();



  menu_principal();
  remove_arquivos();
}

/*Função reponsável por apagar os arquivos auxilires do computador, a fim de não causar um "spam" de arquivos novos no computador do usuário.*/
void remove_arquivos(){
  if (remove(lista_adultos) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_criancas) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_femininos) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_masculinos) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_sobreviventes_adultos) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_nsobreviventes_adultos) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_sobreviventes_criancas) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_nsobreviventes_criancas) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_sobreviventes_femininos) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_nsobreviventes_femininos) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_sobreviventes_masculinos) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_nsobreviventes_masculinos) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_passageiros_1st) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_passageiros_2nd) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_passageiros_3rd) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  if (remove(lista_passageiros_tripulacao) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
}

/*Função geral reponsável por limpar todo o conteúdo de um arquivo ".txt" selecionado.*/
void limpar_arquivo(char *caminho_arquivo) {
  // remove o arquivo original
  if (remove(caminho_arquivo) != 0) {
    printf("Erro ao remover o arquivo.\n");
    return;
  }
  // cria um novo arquivo vazio com o mesmo nome
  FILE *arquivo = fopen(caminho_arquivo, "w");
  if (arquivo == NULL) {
      printf("Erro ao criar o novo arquivo.\n");
      return;
  }
  fclose(arquivo);
}

/*Função usada para limpar todo o conteúdo dos arquivos necessários.*/
void limpar_arquivos(){
  FILE *teste_arquivo;

  if (valida_arquivo(lista_adultos) == 1){
    teste_arquivo = fopen(lista_adultos, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_adultos);
  }else{
    fopen(lista_adultos, abrir);
    fclose(lista_adultos);
    limpar_arquivo(lista_adultos);
  }
  if (valida_arquivo(lista_criancas) == 1){
    teste_arquivo = fopen(lista_criancas, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_criancas);
  }else{
    fopen(lista_criancas, abrir);
    fclose(lista_criancas);
    limpar_arquivo(lista_criancas);
  }
  if (valida_arquivo(lista_femininos) == 1){
    teste_arquivo = fopen(lista_femininos, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_femininos);
  }else{
    fopen(lista_femininos, abrir);
    fclose(lista_femininos);
    limpar_arquivo(lista_femininos);
  }
  if (valida_arquivo(lista_masculinos) == 1){
    teste_arquivo = fopen(lista_masculinos, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_masculinos);
  }else{
    fopen(lista_masculinos, abrir);
    fclose(lista_masculinos);
    limpar_arquivo(lista_masculinos);
  }
  if (valida_arquivo(lista_passageiros_1st) == 1){
    teste_arquivo = fopen(lista_passageiros_1st, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_passageiros_1st);
  }else{
    fopen(lista_passageiros_1st, abrir);
    fclose(lista_passageiros_1st);
    limpar_arquivo(lista_passageiros_1st);
  }
  if (valida_arquivo(lista_passageiros_2nd) == 1){
    teste_arquivo = fopen(lista_passageiros_2nd, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_passageiros_2nd);
  }else{
    fopen(lista_passageiros_2nd, abrir);
    fclose(lista_passageiros_2nd);
    limpar_arquivo(lista_passageiros_2nd);
  }
  if (valida_arquivo(lista_passageiros_3rd) == 1){
    teste_arquivo = fopen(lista_passageiros_3rd, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_passageiros_3rd);
  }else{
    fopen(lista_passageiros_3rd, abrir);
    fclose(lista_passageiros_3rd);
    limpar_arquivo(lista_passageiros_3rd);
  }
  if (valida_arquivo(lista_passageiros_tripulacao) == 1){
    teste_arquivo = fopen(lista_passageiros_tripulacao, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_passageiros_tripulacao);
  }else{
    fopen(lista_passageiros_tripulacao, abrir);
    fclose(lista_passageiros_tripulacao);
    limpar_arquivo(lista_passageiros_tripulacao);
  }
  if (valida_arquivo(lista_sobreviventes_adultos) == 1){
    teste_arquivo = fopen(lista_sobreviventes_adultos, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_sobreviventes_adultos);
  }else{
    fopen(lista_sobreviventes_adultos, abrir);
    fclose(lista_sobreviventes_adultos);
    limpar_arquivo(lista_sobreviventes_adultos);
  }
  if (valida_arquivo(lista_sobreviventes_criancas) == 1){
    teste_arquivo = fopen(lista_sobreviventes_criancas, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_sobreviventes_criancas);
  }else{
    fopen(lista_sobreviventes_criancas, abrir);
    fclose(lista_sobreviventes_criancas);
    limpar_arquivo(lista_sobreviventes_criancas);
  }
  if (valida_arquivo(lista_sobreviventes_femininos) == 1){
    teste_arquivo = fopen(lista_sobreviventes_femininos, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_sobreviventes_femininos);
  }else{
    fopen(lista_sobreviventes_femininos, abrir);
    fclose(lista_sobreviventes_femininos);
    limpar_arquivo(lista_sobreviventes_femininos);
  }
  if (valida_arquivo(lista_sobreviventes_masculinos) == 1){
    teste_arquivo = fopen(lista_sobreviventes_masculinos, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_sobreviventes_masculinos);
  }else{
    fopen(lista_sobreviventes_masculinos, abrir);
    fclose(lista_sobreviventes_masculinos);
    limpar_arquivo(lista_sobreviventes_masculinos);
  }
  if (valida_arquivo(lista_nsobreviventes_adultos) == 1){
    teste_arquivo = fopen(lista_nsobreviventes_adultos, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_nsobreviventes_adultos);
  }else{
    fopen(lista_nsobreviventes_adultos, abrir);
    fclose(lista_nsobreviventes_adultos);
    limpar_arquivo(lista_nsobreviventes_adultos);
  }
  if (valida_arquivo(lista_nsobreviventes_criancas) == 1){
    teste_arquivo = fopen(lista_nsobreviventes_criancas, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_nsobreviventes_criancas);
  }else{
    fopen(lista_nsobreviventes_criancas, abrir);
    fclose(lista_nsobreviventes_criancas);
    limpar_arquivo(lista_nsobreviventes_criancas);

  }
  if (valida_arquivo(lista_nsobreviventes_femininos) == 1){
    teste_arquivo = fopen(lista_nsobreviventes_femininos, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_nsobreviventes_femininos);
  }else{
    fopen(lista_nsobreviventes_femininos, abrir);
    fclose(lista_nsobreviventes_femininos);
    limpar_arquivo(lista_nsobreviventes_femininos);
  }
  if (valida_arquivo(lista_nsobreviventes_masculinos) == 1){
    teste_arquivo = fopen(lista_nsobreviventes_masculinos, abrir);
    fclose(teste_arquivo);
    limpar_arquivo(lista_nsobreviventes_masculinos);
  }else{
    fopen(lista_nsobreviventes_masculinos, abrir);
    fclose(lista_nsobreviventes_masculinos);
    limpar_arquivo(lista_nsobreviventes_masculinos);
  }
}

/*Função reponsável por verificar repetição no cadastro de usuários.*/
char verifica_usuario(char login[20]) {
  FILE *admin_r;
  char linha[50];

  admin_r = fopen(admin, leitura);

  while (fgets(linha, 50, admin_r) != NULL) {
    if (strcmp(linha, login) == 0) {
      printf("\nEste nome de usuário já está cadastrado.\n"); //avisa somente uma vez
    }else
      return login[20];
  }
  fclose(admin_r);
}

/*Função reponsável por cadastrar novos usuários e adicionar seus dados em Admin.txt.*/
void cadastro_sistema(){
  FILE *admin_a;
  char login[20], senha[20];
  admin_a = fopen(admin, abrir);

      if (admin_a != NULL) {
        printf("\nColoque o nome de usuário(SEM ESPAÇAMENTOS):");
        scanf("%s", login);
        verifica_usuario(login);
        printf("\nColoque a senha do usuário(SEM ESPAÇAMENTOS):");
        scanf("%s", senha);
        fprintf(admin_a, "%s:%s:\n", login, senha);

        system("cls");
        printf("\nLOGIN PRONTO!\n\n");
        fclose(admin_a);
      } else {
        printf("\nO arquivo não pode ser aberto.\n");
      }
}

/*Função reponsável por checar se o usuários e senha inseridos pelo operador são compatíveis com a base de dados de Admin.txt.*/
int entrar_sistema(){

  FILE *admin_r;
  char linha[50], login[20], senha[20];
  char* token;

  admin_r = fopen(admin, leitura); // abre o arquivo para leitura

  if (admin_r == NULL) {
    printf("Erro ao abrir o arquivo.\n");
    return 0;
  }

  printf("\nDigite o login do usuário:");
  scanf("%s", login);
  printf("\nDigite a senha do usuário:");
  scanf("%s", senha);
  while (fgets(linha, 50, admin_r) != NULL) {
    token = strtok(linha, ":");                         // Divide a linha em login e senha usando ':'
    if (token != NULL && strcmp(token, login) == 0) {   // Verifica se o login é igual ao procurado
        token = strtok(NULL,":");
        if (strcmp(token, senha) == 0) {                // Verifica se a senha é igual à procurada
            if(token != NULL){
              fclose(admin_r);                          // Fecha o arquivo
              return 1;                                 // Login e senha encontrados
            }else{
              printf("\nNenhuma senha inserida");
            }
        }
      }
    }
    fclose(admin_r); // fecha o arquivo
}

/*Função reponsável por checar se o usuários e senha inseridos pelo operador são compatíveis com a base de dados de Admin.txt.*/
void verifica_idade_struct(){
  FILE *passageiros_r;
  char linha[50];
  char *token;
  char delim[] = ","; // Delimitador das vírgulas
  int numero, cont = 0;

  passageiros_r = fopen(passageiros, leitura);

  if (passageiros_r != NULL){
    while (fgets(linha, 50, passageiros_r) != NULL) {
      token = strtok(linha+1, delim); // Extrai o primeiro token
      while (token != NULL) {
        if (sscanf(token, "%d", &numero) == 1) {
        psg[cont].idade = numero;
          }
          token = strtok(NULL, delim); // Extrai o próximo token
        }
        cont++;
      }
    }else{
    printf("\nO arquivo não pode ser aberto");
  }
  fclose(passageiros_r);
}

/*Função reponsável por checar os arquivos auxiliares quanto ao sexo e situação(vivo ou morto).*/
void verifica_sexo_e_situacao_txt(){

  FILE *passageiros_r,*lista_masculino,*sobreviventes_masculinos,*nsobreviventes_masculinos,*lista_feminino,*sobreviventes_femininos,*nsobreviventes_femininos;
  char linha[50];
  int cont=0;
  passageiros_r = fopen(passageiros, leitura);
  rewind(passageiros_r); //redefine ponteiro de contagem de linha do arquivo

  if (passageiros_r != NULL) {
    while (fgets(linha, 50, passageiros_r) != NULL) {
        if (strstr(linha, "masculino") != NULL) {
          //adiciona em lista masculina
          lista_masculino = fopen(lista_masculinos, abrir);
          fprintf(lista_masculino, "%s", linha);
          fclose(lista_masculino);
          if (strstr(linha, "sim") != NULL){
            //adiciona em arquivo homem vivo
            sobreviventes_masculinos = fopen(lista_sobreviventes_masculinos, abrir);
            fprintf(sobreviventes_masculinos, "%s", linha);
            fclose(sobreviventes_masculinos);
          }else{
            //adiciona em arquivo homem morto
            nsobreviventes_masculinos = fopen(lista_nsobreviventes_masculinos, abrir);
            fprintf(nsobreviventes_masculinos, "%s", linha);
            fclose(nsobreviventes_masculinos);
          }

        }else if(strstr(linha, "feminino") != NULL){
          lista_feminino = fopen(lista_femininos, abrir);
          fprintf(lista_feminino, "%s", linha);
          fclose(lista_feminino);
          if (strstr(linha, "sim") != NULL){
            //adiciona em arquivo mulher vivo
            sobreviventes_femininos = fopen(lista_sobreviventes_femininos, abrir);
            fprintf(sobreviventes_femininos, "%s", linha);
            fclose(sobreviventes_femininos);
          }else{
            //adiciona em arquivo mulher morto
            nsobreviventes_femininos = fopen(lista_nsobreviventes_femininos, abrir);
            fprintf(nsobreviventes_femininos, "%s", linha);
            fclose(nsobreviventes_femininos);
            }
        }
      cont++;
    }
  }else{
        printf("Não foi possível abrir o arquivo");
  }

  fclose(passageiros_r);
}

/*Função reponsável por checar o vetor dos passageiros quanto ao sexo e situação.*/
void verifica_sexo_e_situacao_struct(){

  FILE *passageiros_r;
  char linha[50];
  int cont=0;
  passageiros_r = fopen(passageiros, leitura);
  rewind(passageiros_r); //redefine ponteiro de contagem de linha do arquivo

  if (passageiros_r != NULL) {
    while (fgets(linha, 50, passageiros_r) != NULL) {
        if (strstr(linha, "masculino") != NULL) {
          //adiciona em struct como masculino
          psg[cont].sexo = 0;
          if (strstr(linha, "sim") != NULL){
            //adiciona em struct homem vivo
            psg[cont].situacao = 1;
          }else{
            //adiciona em struct homem morto
            psg[cont].situacao = 0;
          }
        }else if(strstr(linha, "feminino") != NULL){
          //adiciona em struct como feminino
          psg[cont].sexo = 1;
          if (strstr(linha, "sim") != NULL){
            //adiciona em struct mulher vivo
            psg[cont].situacao = 1;
          }else{
            //adiciona em struct mulher morto
            psg[cont].situacao = 0;
            }
        }
      cont++;
    }
  }else{
        printf("Não foi possível abrir o arquivo");
  }
  fclose(passageiros_r);
}

/*Função reponsável por checar os arquivos auxiliares quanto à classe(1st, 2nd, 3rd).*/
void verifica_classe_txt(){
  FILE *passageiros_r, *passageiros_1st, *passageiros_2nd, *passageiros_3rd, *passageiros_tripulacao;
  char linha[50];
  int cont=0;

  passageiros_r = fopen(passageiros, leitura);

  if (passageiros_r != NULL) {
      //verifica passageiros 1,2,3 classe
      while (fgets(linha, 50, passageiros_r) != NULL){
        if(strstr(linha, "1st") != NULL){
          //adiciona em arquivo passageiros 1st
          passageiros_1st = fopen(lista_passageiros_1st, abrir);
          fprintf(passageiros_1st, "%s", linha);
          fclose(passageiros_1st);
        }else if(strstr(linha, "2nd") != NULL){
          //adiciona em arquivo passageiros 2nd
          passageiros_2nd = fopen(lista_passageiros_2nd, abrir);
          fprintf(passageiros_2nd, "%s", linha);
          fclose(passageiros_2nd);
        }else if(strstr(linha, "3rd") != NULL){
          //adiciona em arquivo passageiros 3rd
          passageiros_3rd = fopen(lista_passageiros_3rd, abrir);
          fprintf(passageiros_3rd, "%s", linha);
          fclose(passageiros_3rd);
        }else if(strstr(linha, "trip") != NULL){
          //adiciona em arquivo passageiros tripulação
          passageiros_tripulacao = fopen(lista_passageiros_tripulacao, abrir);
          fprintf(passageiros_tripulacao, "%s", linha);
          fclose(passageiros_tripulacao);
        }
        cont++;
      }
  }else{
      printf("Não foi possível abrir o arquivo");
  }
  rewind(passageiros_r); //redefine ponteiro de contagem de linha do arquivo
  fclose(passageiros_r);
}

/*Função reponsável por checar o vetor dos passageiros quanto à classe.*/
void verifica_classe_struct(){
  FILE *passageiros_r;
  char linha[50];
  int cont=0;

  passageiros_r = fopen(passageiros, leitura);

  if (passageiros_r != NULL) {

      while (fgets(linha, 50, passageiros_r) != NULL){
        if(strstr(linha, "1st") != NULL){
          //adiciona em struct passageiros 1st
          psg[cont].classe = 1;
        }else if(strstr(linha, "2nd") != NULL){
          //adiciona em struct passageiros 2nd
          psg[cont].classe = 2;
        }else if(strstr(linha, "3rd") != NULL){
          //adiciona em struct passageiros 3rd
          psg[cont].classe = 3;
        }else if(strstr(linha, "trip") != NULL){
          //adiciona em struct passageiros tripulação
          psg[cont].classe = 4;
        }
        cont++;
      }
  }else{
      printf("Não foi possível abrir o arquivo");
  }
  rewind(passageiros_r); //redefine ponteiro de contagem de linha do arquivo
  fclose(passageiros_r);
}

/*Função reponsável pela impressão dos passegeiros quanto à faixa etária.*/
void mostrar_faixa_etaria_e_sexo(){
  FILE *passageiros_r;

  int cont=0,cont_homem_adulto = 0, cont_mulher_adulto = 0, cont_homem_crianca = 0, cont_mulher_crianca = 0, cont_criancas = 0, cont_adultos = 0;
  char linha[50];
  passageiros_r = fopen(passageiros, leitura);
  if (passageiros_r != NULL) {

    cont = 0;
    while (fgets(linha, 50, passageiros_r) != NULL) {
     //printf("\nPsg número %d: ", cont+1);
      if(psg[cont].sexo == 0){
        //printf("\nSexo: Masculino, ");
        if(psg[cont].idade <= 16){
          cont_homem_crianca++;
          cont_criancas++;
        }else{
          cont_homem_adulto++;
          cont_adultos++;
        }
      }
      cont++;
    }

    cont=0;
    rewind(passageiros_r);
    while (fgets(linha, 50, passageiros_r) != NULL) {
      if(psg[cont].sexo == 1){
        //printf("\nSexo: Feminino, ");
        if(psg[cont].idade <= 16){
          cont_mulher_crianca++;
          cont_criancas++;
        }else{
          cont_mulher_adulto++;
          cont_adultos++;
        }
      }
      cont++;
    }
    printf("\nTotal de crianças: %d\n-Meninos: %d\n-Meninas: %d\n\nTotal de adultos: %d\n-Homens: %d\n-Mulheres: %d\n", cont_criancas, cont_homem_crianca, cont_mulher_crianca, cont_adultos,cont_homem_adulto, cont_mulher_adulto);
  }else{
    printf("Não foi possível abrir o arquivo");
  }

  fclose(passageiros_r);
}

/*Função geral reponsável pela verificação dos arquivos quanto sua validade para uso.*/
int valida_arquivo(char *nome_arquivo) {

    if (nome_arquivo == NULL) {
      printf("Não foi possível abrir o arquivo %s\n", nome_arquivo);
      return 0;
    } else {

      return 1;
    }
}

/*Função reponsável pela verificação no vetor dos passageiros quanto à idade.*/
void verifica_faixa_etaria_struct(){
  FILE *passageiros_r;
  char linha[50];
  int cont = 0;

  passageiros_r = fopen(passageiros, leitura);
   if (valida_arquivo(passageiros_r) == 1){
      while (fgets(linha, 50, passageiros_r) != NULL) {
        if(psg[cont].idade <=16){
          psg[cont].faixa_etaria = 0;//Criança = 0
        }else{
          psg[cont].faixa_etaria = 1;//Adulto = 0
        }
        cont++;
      }
   }
  fclose(passageiros_r);
}

/*Função reponsável pela verificação no arquivo auxiliar relacionado as idades.*/
void verifica_faixa_etaria_txt(){
  FILE *passageiros_r, *criancas, *adultos, *sobreviventes_criancas, *sobreviventes_adultos, *nsobreviventes_criancas, *nsobreviventes_adultos;
  char linha[20];
  int cont = 0;


  passageiros_r = fopen(passageiros, leitura);
   if (valida_arquivo(passageiros_r) == 1){
      while (fgets(linha, 50, passageiros_r) != NULL) {
        if(psg[cont].idade <=16){
          criancas = fopen(lista_criancas, abrir);
          fprintf(criancas, "%s", linha);
          fclose(criancas);

          if(psg[cont].situacao == 0){
            nsobreviventes_criancas = fopen(lista_nsobreviventes_criancas, abrir);
            fprintf(nsobreviventes_criancas, "%s", linha);
            fclose(nsobreviventes_criancas);
          }else{
            sobreviventes_criancas = fopen(lista_sobreviventes_criancas, abrir);
            fprintf(sobreviventes_criancas, "%s", linha);
            fclose(sobreviventes_criancas);
          }
        }else{
          adultos = fopen(lista_adultos, abrir);
          fprintf(adultos, "%s", linha);
          fclose(adultos);
          if(psg[cont].situacao == 0){
            nsobreviventes_adultos = fopen(lista_nsobreviventes_adultos, abrir);
            fprintf(nsobreviventes_adultos, "%s", linha);
            fclose(nsobreviventes_adultos);
          }else{
            sobreviventes_adultos = fopen(lista_sobreviventes_adultos, abrir);
            fprintf(sobreviventes_adultos, "%s", linha);
            fclose(sobreviventes_adultos);
        }

        }
      cont++;
    }
   }
  fclose(passageiros_r);
}

/*Função reponsável pela impressão dos passegeiros quanto ao sexo.*/
void exibe_sexo(){
  
  FILE *lista_feminino, *lista_masculino;
  char linha[50];
  int cont = 0, contagem_masculino = 0, contagem_feminino = 0;
  lista_feminino = fopen(lista_femininos, leitura);
    if (valida_arquivo(lista_feminino) == 1){
      cont=0;
      while (fgets(linha, 50, lista_feminino) != NULL){
        cont++;
      }
      contagem_feminino = cont+1;
      printf("Número de passageiros mulheres: %d\n", cont);
      fclose(lista_feminino);

    }
    lista_masculino = fopen(lista_masculinos, leitura);
    if (valida_arquivo(lista_masculino) == 1){
      cont=0;
      while (fgets(linha, 50, lista_masculino) != NULL){
        cont++;
      }
      contagem_masculino = cont;
      printf("Número de passageiros homens: %d\n", cont);
      fclose(lista_masculino);

    }
    mostrar_faixa_etaria_e_sexo();
}

/*Função reponsável pela impressão dos passegeiros quanto à classe.*/
void exibe_classe(){
  
    FILE *passageiros_1st, *passageiros_2nd, *passageiros_3rd, *passageiros_tripulacao;
    int cont=0, contagem_passageiros_1st = 0, contagem_passageiros_2nd = 0, contagem_passageiros_3rd, contagem_passageiros_tripulacao = 0, 
    contagem_feminino = 0, contagem_masculino = 0, contagem_crianca=0, contagem_adulto=0,contagem_masculino_crianca=0,
    contagem_feminino_crianca=0, contagem_masculino_adulto=0, contagem_feminino_adulto=0;
    char linha[50];

    passageiros_1st = fopen(lista_passageiros_1st, leitura);
    if(valida_arquivo(passageiros_1st) == 1){
        cont=0;
        while (fgets(linha, 50, passageiros_1st) != NULL){
            cont++;
        }
        contagem_passageiros_1st = cont;
        printf("Número de passageiros da primeira classe: %d\n", cont);
    }
    fclose(passageiros_1st);

    passageiros_2nd = fopen(lista_passageiros_2nd, leitura);
    if(valida_arquivo(passageiros_2nd) == 1){
        cont=0;
        while (fgets(linha, 50, passageiros_2nd) != NULL){
           cont++;
        }
        contagem_passageiros_2nd = cont;
        printf("Número de passageiros da segunda classe: %d\n", cont);
        fclose(passageiros_2nd);
    }

    passageiros_3rd = fopen(lista_passageiros_3rd, leitura);
    if(valida_arquivo(passageiros_3rd) == 1){
        cont=0;
        while (fgets(linha, 50, passageiros_3rd) != NULL){
            cont++;
        }
        contagem_passageiros_3rd = cont;
        printf("Número de passageiros da terceira classe: %d\n", cont);
        fclose(passageiros_3rd);
    }

    passageiros_tripulacao = fopen(lista_passageiros_tripulacao, leitura);
    if(valida_arquivo(passageiros_tripulacao) == 1){
        cont=0;
        while (fgets(linha, 50, passageiros_tripulacao) != NULL){
            cont++;
        }
        contagem_passageiros_tripulacao = cont;
        printf("Número de passageiros tripulação: %d\n", cont);
        fclose(passageiros_tripulacao);
    }

    passageiros_1st = fopen(lista_passageiros_1st, leitura);
    if(valida_arquivo(passageiros_1st) == 1){
        cont=0,contagem_feminino = 0, contagem_masculino = 0;
        while (fgets(linha, 50, passageiros_1st) != NULL){
            if (strstr(linha, "masculino") != NULL){
            contagem_masculino++;
            }else{
                contagem_feminino++;
            }
            cont++;
        }
        printf("\nTotal de passageiros 1st: %d\n -Masculinos: %d\n -Femininos: %d\n", contagem_passageiros_1st, contagem_masculino, contagem_feminino);
        fclose(passageiros_1st);
      }

    passageiros_2nd = fopen(lista_passageiros_2nd, leitura);
    if(valida_arquivo(passageiros_1st) == 1){
        cont=0,contagem_feminino = 0, contagem_masculino = 0;
        while (fgets(linha, 50, passageiros_2nd) != NULL){
            if (strstr(linha, "masculino") != NULL){
            contagem_masculino++;
            }else{
                contagem_feminino++;
            }
            cont++;
        }
        printf("\nTotal de passageiros 2nd: %d\n -Masculinos: %d\n -Femininos: %d\n", contagem_passageiros_2nd, contagem_masculino, contagem_feminino);
        fclose(passageiros_2nd);
    }
    
    passageiros_3rd = fopen(lista_passageiros_3rd, leitura);
    if(valida_arquivo(passageiros_3rd) == 1){
        cont=0,contagem_feminino = 0, contagem_masculino = 0;
        while (fgets(linha, 50, passageiros_3rd) != NULL){
            if (strstr(linha, "masculino") != NULL){
            contagem_masculino++;
            }else{
                contagem_feminino++;
            }
            cont++;
        }
        printf("\nTotal de passageiros 3rd: %d\n -Masculinos: %d\n -Femininos: %d\n", contagem_passageiros_3rd, contagem_masculino, contagem_feminino);
        fclose(passageiros_3rd);
      }

    passageiros_tripulacao = fopen(lista_passageiros_tripulacao, leitura);
    if(valida_arquivo(passageiros_tripulacao) == 1){
        cont=0,contagem_feminino = 0, contagem_masculino = 0;
        while (fgets(linha, 50, passageiros_tripulacao) != NULL){
            if (strstr(linha, "masculino") != NULL){
                contagem_masculino++;
            }else{
                contagem_feminino++;
            }
          cont++;
        }

        printf("\nTotal de passageiros tripulacao: %d\n -Masculinos: %d\n -Femininos: %d\n", contagem_passageiros_tripulacao, contagem_masculino, contagem_feminino);
        fclose(passageiros_tripulacao);
      }

    passageiros_1st = fopen(lista_passageiros_1st, leitura);
        if(valida_arquivo(passageiros_1st) == 1){
        while (fgets(linha, 50, passageiros_1st) != NULL){
            if (psg[cont].idade <= 16){
            contagem_crianca++;
            }else{
            contagem_adulto++;
            }
            cont++;
        }
        printf("\nTotal de passageiros 1st: %d\n -Crianças: %d\n -Adultos: %d\n", contagem_passageiros_1st, contagem_crianca, contagem_adulto);
        fclose(passageiros_1st);
    }

    passageiros_2nd = fopen(lista_passageiros_2nd, leitura);
        if(valida_arquivo(passageiros_2nd) == 1){
            contagem_crianca=0, contagem_adulto=0;
            while (fgets(linha, 50, passageiros_2nd) != NULL){
                if (psg[cont].idade <= 16){
                    contagem_crianca++;
                }else{
                    contagem_adulto++;
                }
                cont++;
            }
        printf("\nTotal de passageiros 2nd: %d\n -Crianças: %d\n -Adultos: %d\n", contagem_passageiros_2nd, contagem_crianca, contagem_adulto);
        fclose(passageiros_2nd);
        }

    passageiros_3rd = fopen(lista_passageiros_3rd, leitura);
        if(valida_arquivo(passageiros_3rd) == 1){
            contagem_crianca=0, contagem_adulto=0;
            while (fgets(linha, 50, passageiros_3rd) != NULL){
                if (psg[cont].idade <= 16){
                    contagem_crianca++;
                }else{
                    contagem_adulto++;
                }
                cont++;
            }     
      printf("\nTotal de passageiros 3rd: %d\n -Crianças: %d\n -Adultos: %d\n", contagem_passageiros_3rd, contagem_crianca, contagem_adulto);
      fclose(passageiros_3rd);
        }

    passageiros_tripulacao = fopen(lista_passageiros_tripulacao, leitura);
    if(valida_arquivo(passageiros_tripulacao) == 1){
        cont=0,contagem_crianca=0, contagem_adulto=0;
        while (fgets(linha, 50, passageiros_tripulacao) != NULL){
            if (psg[cont].idade <= 16){
                contagem_crianca++;
            }else{
                contagem_adulto++;
            }
            cont++;
        }
    printf("\nTotal de passageiros tripulação: %d\n -Crianças: %d\n -Adultos: %d\n", contagem_passageiros_tripulacao, contagem_crianca, contagem_adulto);
    fclose(passageiros_tripulacao);
    }

    passageiros_tripulacao = fopen(lista_passageiros_tripulacao, leitura);
    if(valida_arquivo(passageiros_tripulacao) == 1){
        cont = 0,contagem_feminino = 0, contagem_masculino = 0, contagem_crianca = 0, contagem_adulto = 0;
        while (fgets(linha, 50, passageiros_tripulacao) != NULL){
            if (psg[cont].sexo == 0){
                if (psg[cont].idade <= 16){
                    contagem_masculino_crianca++;
                }else{
                    contagem_masculino_adulto++;
                }
            }else{
                if (psg[cont].idade <= 16){
                    contagem_feminino_crianca++;
                }else{
                    contagem_feminino_adulto++;
                }
            }
        cont++;
      }
      printf("\nTotal de passageiros Tripulação: %d\n -Masculino criança: %d\n -Masculino adulto: %d\n -Feminino criança %d\n -Feminino adulto: %d\n", contagem_passageiros_tripulacao, contagem_masculino_crianca, contagem_masculino_adulto, contagem_feminino_crianca, contagem_feminino_adulto);
      fclose(passageiros_tripulacao);
      }
}

/*Função reponsável pela impressão dos passegeiros quanto à situação de vida.*/
void exibe_situacao(){
  char linha[50];
 
  FILE *sobreviventes_criancas, *nsobreviventes_criancas, *sobreviventes_adultos, *nsobreviventes_adultos, *passageiros_r,
       *sobreviventes_masculinos, *nsobreviventes_masculinos, *sobreviventes_femininos, *nsobreviventes_femininos, *passageiros_tripulacao;
  int cont=0, contagem_passageiros_mortos = 0, contagem_passageiros_vivos = 0, contagem_passageiros_masculino_mortos=0,
      contagem_passageiros_masculino_vivos=0, contagem_passageiros_feminino_mortos=0, contagem_passageiros_feminino_vivos =0,
      contagem_sobreviventes_criancas = 0, contagem_nsobreviventes_criancas = 0, contagem_criancas=0, contagem_sobreviventes_adultos = 0,
      contagem_nsobreviventes_adultos=0, contagem_adultos =0, contagem_passageiro_tripulacao_vivos=0,
      contagem_passageiro_tripulacao_mortos = 0, contagem_tripulacao = 0;

    passageiros_r = fopen(passageiros, leitura);
    if(valida_arquivo(passageiros_r) == 1){
        cont=0;
        while (fgets(linha, 50, passageiros_r) != NULL){
            if(strstr(linha, "sim") != NULL){
                contagem_passageiros_vivos++;
            }else{
                contagem_passageiros_mortos++;
                }
                cont++;
            }
            printf("SITUAÇÃO GERAL DOS PASSAGEIROS (%d):\n", cont);
            printf(" -Passageiros mortos: %d\n", contagem_passageiros_mortos);
            printf(" -Passageiros vivos: %d\n\n", contagem_passageiros_vivos);
            fclose(passageiros_r);
            }

    sobreviventes_masculinos = fopen(lista_sobreviventes_masculinos, leitura);
    if(valida_arquivo(sobreviventes_masculinos) == 1){
        while (fgets(linha, 50, sobreviventes_masculinos) != NULL){
            contagem_passageiros_masculino_vivos++;
        }
    fclose(sobreviventes_masculinos);
    }

    nsobreviventes_masculinos = fopen(lista_nsobreviventes_masculinos, leitura);
    if(valida_arquivo(nsobreviventes_masculinos) == 1){
        while (fgets(linha, 50, sobreviventes_masculinos) != NULL){
            contagem_passageiros_masculino_mortos++;
        }
    fclose(nsobreviventes_masculinos);
    }

    sobreviventes_femininos = fopen(lista_sobreviventes_femininos, leitura);
    if(valida_arquivo(sobreviventes_femininos) == 1){
        while (fgets(linha, 50, sobreviventes_masculinos) != NULL){
            contagem_passageiros_feminino_vivos++;
        }
    fclose(sobreviventes_femininos);
    }

    nsobreviventes_femininos = fopen(lista_nsobreviventes_femininos, leitura);
    if(valida_arquivo(nsobreviventes_femininos) == 1){
        while (fgets(linha, 50, nsobreviventes_femininos) != NULL){
            contagem_passageiros_feminino_mortos++;
        }
    fclose(nsobreviventes_femininos);
    }

    printf("SITUAÇÃO DOS HOMENS (%d) :\n", contagem_passageiros_masculino_mortos+contagem_passageiros_masculino_vivos);
    printf(" -Homens mortos: %d\n", contagem_passageiros_masculino_mortos);
    printf(" -Homens vivos: %d\n\n", contagem_passageiros_masculino_vivos);
    printf("SITUAÇÃO DAS MULHERES (%d) :\n", contagem_passageiros_feminino_vivos+contagem_passageiros_feminino_mortos);
    printf(" -Mulheres vivas: %d\n", contagem_passageiros_feminino_vivos);
    printf(" -Mulheres mortas: %d\n\n", contagem_passageiros_feminino_mortos);

    sobreviventes_criancas = fopen(lista_sobreviventes_criancas, leitura);
    if(valida_arquivo(sobreviventes_criancas) == 1){
        while (fgets(linha, 50, sobreviventes_criancas) != NULL){
            contagem_sobreviventes_criancas++;
            contagem_criancas++;
            }
        }
    fclose(sobreviventes_criancas);

    nsobreviventes_criancas = fopen(lista_nsobreviventes_criancas, leitura);
    if(valida_arquivo(nsobreviventes_criancas) == 1){
        while (fgets(linha, 50, nsobreviventes_criancas) != NULL){
            contagem_nsobreviventes_criancas++;
            contagem_criancas++;
            }
            printf("SITUAÇÃO DAS CRIANÇAS (%d):\n -Vivas: %d\n -Mortas: %d", contagem_criancas, contagem_sobreviventes_criancas,
            contagem_nsobreviventes_criancas);
        }
        fclose(nsobreviventes_criancas);

        sobreviventes_adultos = fopen(lista_sobreviventes_adultos, leitura);
        if(valida_arquivo(sobreviventes_adultos) == 1){
            while (fgets(linha, 50, sobreviventes_adultos) != NULL){
                contagem_sobreviventes_adultos++;
                contagem_adultos++;
                }
        }
        fclose(sobreviventes_adultos);

        nsobreviventes_adultos = fopen(lista_nsobreviventes_adultos, leitura);
        if(valida_arquivo(nsobreviventes_adultos) == 1){
            while (fgets(linha, 50, nsobreviventes_adultos) != NULL){
                contagem_nsobreviventes_adultos++;
                contagem_adultos++;
                }
            printf("\n\nSITUAÇÃO DOS ADULTOS (%d):\n -Vivos: %d\n -Mortos: %d", contagem_adultos, contagem_sobreviventes_adultos,
            contagem_nsobreviventes_adultos);
        }
        fclose(nsobreviventes_adultos);

        contagem_tripulacao=0;

        passageiros_tripulacao = fopen(lista_passageiros_tripulacao, leitura);
        if(valida_arquivo(passageiros_tripulacao) == 1){
            while (fgets(linha, 50, passageiros_tripulacao)!= NULL){
                if (strstr(linha, "sim") != NULL){
                    contagem_passageiro_tripulacao_vivos++;
                }else{
                    contagem_passageiro_tripulacao_mortos++;
                    }
                contagem_tripulacao++;
            }
            printf("\n\nSITUAÇÃO DA TRIPULAÇÃO (%d):\n -Vivos: %d\n -Mortos: %d", contagem_tripulacao, contagem_passageiro_tripulacao_vivos,
            contagem_passageiro_tripulacao_mortos);
        }
        fclose(passageiros_tripulacao);
}

/*Função reponsável pelo cálculo da média e mediana.*/
void exibe_estatistica(){
    int totalpsg=0, cont=0, cont_criancas =0, cont_adultos=0 ,somas_idade=0, idade_media=0;
    char linha[50];

    FILE *passageiros_r;
    passageiros_r = fopen(passageiros, leitura);
    if (passageiros_r != NULL) {
        cont = 0;
        while (fgets(linha, 50, passageiros_r) != NULL) {
            somas_idade += psg[cont].idade;
            if(psg[cont].idade <= 16){
                cont_criancas++;
            }else{
                cont_adultos++;
            }
        }
        cont++;
    }
    totalpsg = cont_adultos + cont_criancas;
    idade_media = somas_idade/totalpsg;
    printf("TOTAL DE PASSAGEIROS: %d\n", totalpsg);
    printf("MÉDIA DAS IDADES: %d\n", idade_media);
    ordenar(psg[0].idade,2201);
}

/*Função reponsável pela ordenação das idades e passagem do mesmo para o o uso da próxima função.*/
void ordenar(int *arr, int n){

  int i, j, temp, mediana[2201];
  for (i=0; i<n-1; i++) {
      for (j=0; j<n-i-1; j++) {
          if (psg[j].idade > psg[j+1].idade) {
              temp = psg[j].idade;
              psg[j].idade = psg[j+1].idade;
              psg[j+1].idade = temp;
          }
      }
  }

  for (int i = 0; i < 2201; i++) {
    mediana[i] = psg[i].idade;
  }
  verifica_idade_struct();//retornar idade para o struct que foi ordenado
  median(mediana, 2201);
}

/*Função responsável pelo encontro e impressão e  da mediana*/
void median(int *p, int n) {
    int meio = n / 2;
    int mediana;
    if (n % 2 == 0) {
      mediana = ((p[meio - 1] + p[meio]) / 2);
    } else {
      mediana = p[meio];
    }
    printf("MEDIANA DAS IDADES: %d\n", mediana);
}

/*Função reponsável pelo cálculo das porcentagens em relação aos vivos.*/
void porcentagem_vivos(){

    int i, CMas=0, CFem=0, CCri=0, CAdul=0, CFirst=0, CSec=0, CThr=0, CTri=0,
        CMasV=0, CFemV=0, CCriV=0, CAdulV=0, CFirstV=0, CSecV=0, CThrV=0, CTriV=0;

    for(i=0; i<2201; i++){          //lendo todo o  vetor com os dados dos passageiros para coleta de informações.
        if (psg[i].sexo == 0){
            CMas++;
            if (psg[i].situacao == 1)
            CMasV++;
        }
        if (psg[i].sexo == 1){
            CFem++;
            if (psg[i].situacao == 1)
            CFemV++;
        }
        if (psg[i].idade <= 16){
            CCri++;
            if (psg[i].situacao == 1)
            CCriV++;
        }
        if (psg[i].idade > 16){
            CAdul++;
            if (psg[i].situacao == 1)
            CAdulV++;
        }
        if (psg[i].classe == 1){
            CFirst++;
            if (psg[i].situacao == 1)
            CFirstV++;
        }
        if (psg[i].classe == 2){
            CSec++;
            if (psg[i].situacao == 1)
            CSecV++;
        }
        if (psg[i].classe == 3){
            CThr++;
            if (psg[i].situacao == 1)
            CThrV++;
        }
        if (psg[i].classe == 4){
            CTri++;
            if (psg[i].situacao == 1)
            CTriV++;
        }
    }

    printf("\nHomens Vivos / Homens: %.2f%%\n", (float)CMasV*100/CMas);                 //Impressão dos dados percentuais.
    printf("Homens / Total: %.2f%%\n", (float)CMas*100/2201);
    printf("Homens Vivos / Total: %.2f%%\n", (float)CMasV*100/2201);

    printf("\nMulheres Vivas / Mulheres: %.2f%%\n", (float)CFemV*100/CFem);
    printf("Mulheres / Total: %.2f%%\n", (float)CFem*100/2201);
    printf("Mulheres Vivas / Total: %.2f%%\n", (float)CFemV*100/2201);

    printf("\nCrianças Vivas / Crianças: %.2f%%\n", (float)CCriV*100/CCri);
    printf("Crianças / Total: %.2f%%\n", (float)CCri*100/2201);
    printf("Crianças Vivos / Total: %.2f%%\n", (float)CCriV*100/2201);

    printf("\nAdultos Vivos / Adultos: %.2f%%\n", (float)CAdulV*100/CAdul);
    printf("Adultos / Total: %.2f%%\n", (float)CAdul*100/2201);
    printf("Adultos Vivos / Total: %.2f%%\n", (float)CAdulV*100/2201);

    printf("\nPrimeira Classe Vivos / Primeira Classe: %.2f%%\n", (float)CFirstV*100/CFirst);
    printf("Primeira Classe / Total: %.2f%%\n", (float)CFirst*100/2201);
    printf("Primeira Classe Vivos / Total: %.2f%%\n", (float)CFirstV*100/2201);

    printf("\nSegunda Classe Vivos / Segunda Classe: %.2f%%\n", (float)CSecV*100/CSec);
    printf("Segunda Classe / Total: %.2f%%\n", (float)CSec*100/2201);
    printf("Segunda Classe Vivos / Total: %.2f%%\n", (float)CSecV*100/2201);

    printf("\nTerceira Classe Vivos / Terceira Classe: %.2f%%\n", (float)CThrV*100/CThr);
    printf("Terceira Classe / Total: %.2f%%\n", (float)CThr*100/2201);
    printf("Terceira Classe Vivos / Total: %.2f%%\n", (float)CThrV*100/2201);

    printf("\nTripulação Vivos / Tripulação: %.2f%%\n", (float)CTriV*100/CTri);
    printf("Tripulação / Total: %.2f%%\n", (float)CTri*100/2201);
    printf("Tripulação Vivos / Total: %.2f%%\n", (float)CTriV*100/2201);
}

/*Os dois menus operam o código ao permitir a entrada de duas escolhas do usuário. É bem intuitivo e didático, e como chama quase todas as funções
do sistema, não apresenta grandes linhas de código.*/
void menu_principal(){
  int escolha, escolha2;
  do{
      printf("********BEM VINDO AO SISTEMA TITANIC********\n\n");
      printf("1- Cadastro de usuário\n");
      printf("2- Entrar no sistema\n");
      printf("3- Sair\n");
      printf("\nDigite sua opção: ");
      scanf("%d", &escolha);        //Entrada da primeira escolha.
      switch(escolha){
        case 1:                     //Para cadastros de usuários.
          system("cls");
          printf("\n--CADASTRO DE USUÁRIO:--\n");
          cadastro_sistema();
          break;

        case 2:                     //Permissão para entrar no programa.
          system("cls");
          printf("\n--INSIRA SUAS CREDENCIAIS:--\n");
          if (entrar_sistema() == 1){
            system("cls");
            do{
            printf("\n---- MENU ----\n");           //Entrando no sistema, é solicitada qual informação deve ser mostrada.
            printf("\nOlá usuário!\n");
            printf("\n1- Mostrar estatísticas de sexo\n");
            printf("2- Mostrar estatísticas de classe\n");
            printf("3- Mostrar estatísticas de situação\n");
            printf("4- Estatísticas percentuais\n");
            printf("5- Medidas de tendência central\n");
            printf("6- Voltar\n");
            printf("\nDigite sua opção: ");
            scanf("%d", &escolha2);
                switch(escolha2){

                case 1:                              //Estatísticas baseadas no sexo.
                  system("cls");
                  printf("\n\nEXIBINDO SEXO: \n\n");
                  exibe_sexo();
                  break;
                case 2:                             //Estatísticas baseadas na classe.
                  system("cls");
                  printf("\n\nEXIBINDO CLASSES: \n\n");

                  exibe_classe();
                  break;

                case 3:                             //Estatísticas baseadas na situação.
                  system("cls");
                  printf("\n\nEXIBINDO SITUAÇÃO: \n\n");
                  exibe_situacao();

                  break;

                case 4:                             //Estatísticas específicas dos sobreviventes.
                  system("cls");
                  printf("\n\nEXIBINDO PORCENTAGENS: \n\n");
                  porcentagem_vivos();
                  break;

                case 5:                             //Estatísticas de tendências centrais.
                  system("cls");
                  printf("\n\nEXIBINDO ESTATÍSTICAS: \n\n");
                  exibe_estatistica();
                  break;

                case 6:                             //Volta para o menu anterior.
                  system("cls");
                  printf("\n\n--VOCÊ FOI DESLOGADO--\n\n");
                  break;

                default:                            //Para opções diferentes.
                  system("cls");
                  printf("\n\n--OPÇÃO INVÁLIDA--\n\n");
                  break;
                }
            }while(escolha2 != 6);
          }else{
            system("cls");
            printf("\nNão foi possível entrar no sistema\n");
          }
        break;

        case 3:
            printf("Você saiu do sistema\n");     //Tchau :)
        break;

        default:
          system("cls");
          printf("\n\n--OPÇÃO INVÁLIDA--\n\n");         //Para opções diferentes.
          break;
      }
    }while(escolha!=3);
}
