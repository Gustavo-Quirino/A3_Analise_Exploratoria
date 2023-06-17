# Análise Exploratória PROUNI


![dataset-cover](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/fb4cacee-9406-4b75-8aad-e399ccd52be2)

# 1. Introdução

O Programa Universidade para Todos (ProUni) foi criado em 2004, pela Lei nº 11.096/2005 já ajudou milhares de estudantes pelo Brasil a realizar o sonho de cursar uma faculdade, é um programa onde as faculdades particulares oferecem bolsas de estudos de 50% ou 100% do valor total. 
Neste estudo irei explorar os dados do período de 2005 a 2019 obtidos através originalmente do site https://dados.gov.br/dataset/mec-prouni que está atualmente indisponível, mas foi adaptado do estudo https://www.kaggle.com/datasets/lfarhat/brasil-students-scholarship-prouni-20052019 , onde contém os principais dados necessários para os objetivos deste estudo.


<h4 align="center"> 
</h4>

# 2. Objetivos

O objetivo deste estudo é realizar uma Análise Exploratória dos Dados (Exploratory Data Analysis - EDA) do conjunto de dados do PROUNI no período de 2005-2019, adaptado pelo autor e disponível em https://www.kaggle.com/datasets/lfarhat/brasil-students-scholarship-prouni-20052019; a fim de caracterizar o perfil dos estudantes e quais os cursos mais escolhidos. Especificiamente serão respondidas as seguintes questões de pesquisa:

1. Quantos estudantes foram beneficiados com o programa durante este período?
2. Qual a região com mais estudantes com a bolsa?
3. Qual o curso mais escolhidos com bolsa total? e parcial?
4. Qual a maior porcentagem de bolsas, Parcial ou Integral?
5. Qual a modalidade mais escolhida, EAD ou Presencial?

<h4 align="center"> 

</h4>


# 3. Metodologia

Nesta seção será apresentado todo o processo de preparação, organização e limpeza de dados feito no dataset que possui os seguintes dados:



| Coluna                         | Descrição                                                           | Tipo                      |
|--------------------------------|---------------------------------------------------------------------|---------------------------|
| ANO_CONCESSAO_BOLSA            | Ano em que a bolsa foi condedida                                    | Int                       |
| CODIGO_EMEC_IES_BOLSA          | Código interno número da bolsa                                      | Int                       |
| NOME_IES_BOLSA                 | Nome da faculdade concedente da bolsa                               | String                    | 
| TIPO_BOLSA                     | Informa se a bolsa é parcial ou integral                            | String                    |
| MODALIDADE_ENSINO_BOLSA        | Modalidade escolhida pelo bolsista se a distância ou Presencial     | String                    |
| NOME_CURSO_BOLSA               | Curso escolhido pelo bolsista                                       | String                    | 
| NOME_TURNO_CURSO_BOLSA         | Qual o turno escolhido pelo aluno                                   | String                    |
| CPF_BENEFICIARIO_BOLSA         | CPF criptografado do bolsista                                       | String                    |
| SEXO_BENEFICIARIO_BOLSA        | Sexo declarado do bolsista                                          | String                    | 
| RACA_BENEFICIARIO_BOLSA        | Raça declarada do bolsista                                          | String                    |
| DT_NASCIMENTO_BENEFICIARIO     | Data de nascimento do Bolsista                                      | String                    |
| BENEFICIARIO_DEFICIENTE_FISICO | Bolsista declara se é deficiente físico ou não                      | String                    | 
| REGIAO_BENEFICIARIO_BOLSA      | Região do Brasil onde a faculdade está localizada                   | String                    | 
| SIGLA_UF_BENEFICIARIO_BOLSA    | Estado do Brasil onde a faculdade está localizada                   | String                    |
| MUNICIPIO_BENEFICIARIO_BOLSA   | Município do Brasil onde a faculdade está localizada                | String                    | 
| IDADE                          | Idade do bolsista                                                   | Int                       |


# 3.1 Configuração do Ambiente

Toda a configuração e desenvolvimento foi feita no power BI para a facilitar visualmente a apresentação desse trabalho e será presentada abaixo.

# 3.2 Leitura dos Dados

Os dados vieram em formato CSV e lidos diretamente no power BI para a construção dos visuais apresentados. O arquivo na íntegra também está na pasta arquivo.

# 3.3 Organização e Limpeza dos Dados


## 3.3.1 Remoção de Colunas 

Remoção de colunas incompletas e/ou desnecessárias para a análise.

A Coluna Idade original foi retirada pois não fornecia a idade real  do estudante na data atual, e nem na data citada.

## 3.3.2 Remoção de linhas

Foram removidas 186 linhas de estudantes com informações incompletas.

# 3.4 Mapeamento de dados

Como os dados são todos nacionais não foi necessária nenhuma alteração para que a compreensão ficasse mais fácil.

# 3.5 Feature Engineering

A engenharia de recursos (Feature Engineering) é o processo de usar o conhecimento do domínio para extrair recursos dos dados brutos. Neste estudo não foi necessário criar novos valores.

# 3.6 Tecnologias Usadas

- Power BI

# 4. Análise dos Dados

## 4.1 Quantos estudantes foram beneficiados com o programa durante este período?
## 4.2 Qual a região com mais estudantes com a bolsa?
## 4.3 Qual o curso mais escolhidos com bolsa total? e parcial?
## 4.4 Qual a maior porcentagem de bolsas, Parcial ou Integral?
## 4.5 Qual a modalidade mais escolhida, EAD ou Presencial?



# 5. Conclusão

Como demonstrado acima esse programa foi e ainda é essencial para que estudantes de todo o Brasil possam cursar a faculdade desejada ou uma formação incial para depois poder cursar o que deseja mas já tenha um salário digno e que possa pagar sem que atrapalhe financeiramente sua vida.
Todas as regiões do Brasil são beneficiadas sem exceção e com certeza mudou a vida de todos que souberam e aproveitaram essa oportunidade, mesmo a maioria sendo de bolsas parciais.
Eu imagino que devido a pandemia e demais fatores se os dados fossem atualizados para o dia de hoje a maior mudança seria em relação a modalidade escolhida já que nessa análise o presencial era o mais escolhido.

# Referências

- "https://www.kaggle.com/datasets/lfarhat/brasil-students-scholarship-prouni-20052019"
- "http://portal.mec.gov.br/index.php?option=com_content&view=article&id=205&Itemid=298&msg=1&l=aW5kZXgucGhwP29wdGlvbj1jb21fY29udGVudCZ2aWV3PWJ1c2NhZ2VyYWwmSXRlbWlkPTE2NCZwYXJhbXNbc2VhcmNoX3JlbGV2YW5jZV09cHJvdW5pJmQ9cyZwYXJhbXNbZGVdPSZwYXJhbXNbYXRlXT0mcGFyYW1zW2NhdGlkXT0mcGFyYW1zW3NlYXJjaF9tZXRob2RdPWFsbCZwYXJhbXNbb3JkXT1wcg==#:~:text=O%20Programa%20Universidade%20para%20Todos,institui%C3%A7%C3%B5es%20privadas%20de%20educa%C3%A7%C3%A3o%20superior."

<h4 align="center"> 
	🚧  Em desenvolvimento . . .
</h4>
