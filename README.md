# Análise Exploratória PROUNI


![dataset-cover](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/fb4cacee-9406-4b75-8aad-e399ccd52be2)

# 1. Introdução

O Programa Universidade para Todos (ProUni) foi criado em 2004, pela Lei nº 11.096/2005 já ajudou milhares de estudantes pelo Brasil a realizar o sonho de cursar uma faculdade, é um programa onde as faculdades particulares oferecem bolsas de estudos de 25%, 50% ou 100% do valor total. 
Neste estudo irei explorar os dados do período de 2005 a 2019 obtidos através originalmente do site https://dados.gov.br/dataset/mec-prouni que está atualmente indisponível, mas foi adaptado do estudo https://www.kaggle.com/datasets/lfarhat/brasil-students-scholarship-prouni-20052019 , onde contém os principais dados necessários para os objetivos deste estudo.


# 2. Objetivos

O objetivo deste estudo é realizar uma Análise Exploratória dos Dados (Exploratory Data Analysis - EDA) do conjunto de dados do PROUNI no período de 2005-2019, adaptado pelo autor e disponível em https://www.kaggle.com/datasets/lfarhat/brasil-students-scholarship-prouni-20052019; a fim de caracterizar o perfil dos estudantes e quais os cursos mais escolhidos. Especificiamente serão respondidas as seguintes questões de pesquisa:

1. Quantos estudantes foram beneficiados com o programa durante este período?
2. Qual a região com mais estudantes com a bolsa?
3. Qual o curso mais escolhidos na modalidade presencial? e a distancia?
4. Qual a maior porcentagem de bolsas, Parcial ou Integral?
5. Qual a modalidade mais escolhida, EAD ou Presencial?


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


## 3.1 Configuração do Ambiente

Toda a configuração e desenvolvimento foi feita no power BI para a facilitar visualmente a apresentação desse trabalho e será apresentada abaixo.

## 3.2 Leitura dos Dados

Os dados vieram em formato CSV e lidos diretamente no power BI para a construção dos visuais apresentados.

## 3.3 Organização e Limpeza dos Dados

## 3.3.1 Remoção de Colunas 

A remoção de colunas não foi necessária para este estudo, todas se complementavam e contribuiram para o estudo como um todo.

## 3.3.2 Remoção de linhas

Foram desconsideradas 186 linhas de estudantes com informações incompletas, em alguns estudos demonstrados, para a contagem total de alunos que receberam as bolsas eles foram mantidos na contagem.

## 3.4 Mapeamento de dados

Como os dados são todos nacionais não foi necessária nenhuma alteração para que a compreensão ficasse mais fácil.

## 3.5 Feature Engineering

A engenharia de recursos (Feature Engineering) é o processo de usar o conhecimento do domínio para extrair recursos dos dados brutos. Neste estudo criei uma função de correção para acentos, visto que trocar para Unicode UFT-8 não atingi o objetivo de correção, e mesmo com a criação dessa função demonstrada abaixo a correção não foi possível, já que o erro era direto na escrita do CSV e não os acentos que estavam gerando o erro de formatação, mas mesmo assim foram mantidas as configurações e ações tomadas para tentativa de correção.

```
(texto as text) =>
let
    ComAcentos = Text.ToList("àáâãäèéêëìíîïòóôõöùúûüÀÁÂÃÄÈÉÊËÌÍÎÒÓÔÕÖÙÚÛÜçÇñÑ"),
    SemAcentos = Text.ToList("aaaaaeeeeiiiiooooouuuuAAAAAEEEEIIIOOOOOUUUUcCnN"),
    ParesAcentos = List.Zip({ComAcentos, SemAcentos}),
    TextoQuebrado = Text.ToList(texto),
    Substituicao = List.ReplaceMatchingItems(TextoQuebrado, ParesAcentos),
    Resultado = Text.Combine(Substituicao)
in
    Resultado
```
## 3.6 Tecnologias Usadas

- Power BI

# 4. Análise dos Dados

## 4.1 Quantos estudantes foram beneficiados com o programa durante este período?

![Questao 1](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/cf7377ee-3870-4acd-ba09-fc7f1a660ec2)

No período de 2015 a 2019 Dois Milhões quinhentos e oitenta mil e quarenta alunos foram beneficiados dos quais eu fiz parte desse múmero por isso decidi pesquisar dados sobre esse tema, porém dentro desse número existem 4.375 alunos em que o curso não está preechido e dentro desse número 186 alunos com os quais muitos dados estão em branco, para este número não foram desconsiderados porém, para as demais análises foram retirados já que tinham informações importantes para os dados apresentados.

## 4.2 Qual a região com mais estudantes com a bolsa?

![regiao](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/83fb4636-dad7-4f17-b2fa-06d875943f91)

Teste

## 4.3 Qual o curso mais escolhidos na modalidade presencial? e a distancia?

![Questao 5-1](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/c9b2352c-f939-4da3-813a-07a813a2957e)

Teste

![Questao 5-2](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/5d0331af-e3d6-46f2-8d3d-677ef6437feb)

Teste

## 4.4 Qual a maior porcentagem de bolsas, Parcial ou Integral?

![tipo de bolsa](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/6205f905-26f5-4c1c-849a-f07ce8a8ef16)

Teste

## 4.5 Qual a modalidade mais escolhida, EAD ou Presencial?

![Modalidade](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/2445d5b9-9b39-4e98-b853-1e2f5bca0239)

Teste


# 5. Conclusão

Como demonstrado acima esse programa foi e ainda é essencial para que estudantes de todo o Brasil possam cursar a faculdade desejada ou uma formação incial para depois poder cursar o que deseja mas já tenha um salário digno e que possa pagar sem que atrapalhe financeiramente sua vida.
Todas as regiões do Brasil são beneficiadas sem exceção e com certeza mudou a vida de todos que souberam e aproveitaram essa oportunidade, mesmo a maioria sendo de bolsas parciais.
Eu imagino que devido a pandemia e demais fatores se os dados fossem atualizados para o dia de hoje a maior mudança seria em relação a modalidade escolhida já que nessa análise o presencial era o mais escolhido.

# Referências

- Brasil Students Scholarship - Prouni - (2005-2019). (2022) Disponível em: <https://www.kaggle.com/datasets/lfarhat/brasil-students-scholarship-prouni-20052019>. Acesso em: 18 jun. 2023.
- ProUni - Apresentação. (2018) Disponível em: <http://portal.mec.gov.br/prouni-sp-1364717183/apresentacao>. Acesso em: 18 jun. 2023.
- Visualização de Dados | Microsoft Power BI. (2023) Disponível em: <https://powerbi.microsoft.com/pt-br/>. Acesso em: 18 jun. 2023.
