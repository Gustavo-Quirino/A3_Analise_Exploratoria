# Análise Exploratória PROUNI


![dataset-cover](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/fb4cacee-9406-4b75-8aad-e399ccd52be2)


# Índice/Sumário

* [Introdução](#1-introdução)

# 1. Introdução

O Programa Universidade para Todos (ProUni) foi criado em 2004, pela Lei nº 11.096/2005 já ajudou milhares de estudantes pelo Brasil a realizar o sonho de cursar uma faculdade, é um programa onde as faculdades particulares oferecem bolsas de estudos de 25%, 50% ou 100% do valor total. 
Neste estudo irei explorar os dados do período de 2005 a 2019 obtidos através originalmente do site https://dados.gov.br/dataset/mec-prouni que está atualmente indisponível, mas foi adaptado do estudo https://www.kaggle.com/datasets/lfarhat/brasil-students-scholarship-prouni-20052019 , onde contém os principais dados necessários para os objetivos deste estudo.


# 2. Objetivos

O objetivo deste estudo é realizar uma Análise Exploratória dos Dados (Exploratory Data Analysis - EDA) do conjunto de dados do PROUNI no período de 2005-2019, adaptado pelo autor e disponível em https://www.kaggle.com/datasets/lfarhat/brasil-students-scholarship-prouni-20052019; a fim de caracterizar o perfil dos estudantes e quais os cursos mais escolhidos. Especificiamente serão respondidas as seguintes questões de pesquisa:

1. Quantos estudantes foram beneficiados com o programa durante este período?
2. Qual a região com mais estudantes com a bolsa?
3. Qual o curso mais escolhidos na modalidade presencial? e a distancia?
4. Qual o tipo de bolsa mais oferecida, Parcial ou Integral?
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

A região que mais teve utilização de bolsas foi a região sudeste, apesar de não ser a maior região do Brasil é a região mais populada, isso explica ter mais bolsistas até que a soma das regiões Sul,Nordeste e Centro-Oeste. Porém, isso pode apontar também uma carência das faculdades que oferecem os programas nas demais regiões principamente na região Norte que é onde menos possui bolsistas.

## 4.3 Qual o curso mais escolhidos na modalidade presencial? e a distancia?

![Questao 5-1](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/c9b2352c-f939-4da3-813a-07a813a2957e)

Este foi o modelo que mais deixou evidente uma inconsistência de dados do arquivo, parecia ser um erro de leitura do arquivo devido aos acentos porém, durante as tentativas de ajuste percebi que o erro já era na verdade da digitação do próprio arquivo e não o power BI que estava gerando essas inconsistências. Um exemplo dissoé no curso de Administração, onde deveria aparecer com 243.116 estudantes, porém ele aparece como segundo curso mais buscado presencialmente pelos estudantes com 208.001 alunos inscritos e novamente na 13º posição dessa vez com o nome "AdministraAAo" com 35.116 estudantes. Isso também se aplica a outros cursos com acento no nome e descredibilizou um pouco este resultado. Mas os 10 Cursos mais buscados foram: Direito, Administração, Enfermagem, Pedagogia, Ciências Contábeis, Engenharia Civil, Psicologia, Educação Física, Fisioterapia e Gestão de Recursos Humanos.

![Questao 5-2](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/5d0331af-e3d6-46f2-8d3d-677ef6437feb)

No EAD além do mesmo problema encontrado e descrito no modelo presencial, tivemos também alguns cursos em que continha a nomenclatura EAD na frente do nome, esse foi editado e retirado por meio da ferramente de substituição do power BI e foi resolvido. No modelo a distância os 10 cursos mais buscados foram: Pedagogia, Administração, Gestão de Recursos Humanos, Serviço Social, Ciências Contábeis, Processos Gerenciais, História, Educação Física, Gestão Financeira e Matemática. A classificação foi baseada na soma das duas apresentações quando demonstrada no quadro como por exemplo Serviço Social que apesar de aparecer como quinto mais buscado visualmente na verdade com a soma das duas aparições na demonstração visual ficou como o terceiro mais procurado.

## 4.4 Qual o tipo de bolsa mais oferecida, Parcial ou Integral?

![tipo de bolsa](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/6205f905-26f5-4c1c-849a-f07ce8a8ef16)

As bolsas integrais com 100% do curso grátis foi o tipo mais oferecido, enquanto a bolsa complementar de 25% a com menos estudantes, isso mostra que as faculdades se preocuparam em oferecer a melhor bolsa para que os alunos conseguissem focar mais tempo nos estudos e quando conseguissem um estágio remunerado poder complementar a renda da casa.

## 4.5 Qual a modalidade mais escolhida, EAD ou Presencial?

![Modalidade](https://github.com/Gustavo-Quirino/A3_Analise_Exploratoria/assets/74928403/2445d5b9-9b39-4e98-b853-1e2f5bca0239)

Como no período análisado não tinhamos tanto costume e nem sonhavamos com a pandemia e todas as mudanças que ela gerou, a modalidade mais escolhida pelos alunos e provavelmente a com mais vagas ofertadas pelas faculdades era o modelo presencial, acredito que durante o perído de 2020 a 2022 os números devem estar com uma porcentagem bastante alta também nos cursos a distância.


# 5. Conclusão

Como demonstrado acima esse programa foi e ainda é essencial para que estudantes de todo o Brasil possam cursar a faculdade desejada ou uma formação incial para depois poder cursar o que deseja mas já tenha um salário digno e que possa pagar sem que atrapalhe financeiramente sua vida.
Todas as regiões do Brasil são beneficiadas sem exceção e com certeza mudou a vida de todos que aproveitaram essa oportunidade, como demonstrado a maioria das bolsas que foram cedidas são bolsas totais com 100% de isenção de pagamento para realizar o curso, senti falta de uma coluna de finalização do curso para termos a noção de quantas pessoas conseguiram concluir a formação e ter sua vida transformada pelo programa.
Devido a pandemia e demais fatores se os dados fossem atualizados até 2022 a maior mudança seria que teriamos, acredito que seria em relação a porcentagem da modalidade escolhida já que nessa análise o presencial era o mais escolhido.
Com esses dados mesmo que inconclusivos devido a falta de informações sobre quantos alunos concluiram o curso escolhido, foi muito importante poder demonstrar como ele impactou e mudou a vida de várias pessoas que não tinham condições de relizar um curso superior pagando as mensalidades e demonstrar as diferenças de como foi aproveitado nas diferentes regiões do Brasil.

# Referências

- Brasil Students Scholarship - Prouni - (2005-2019). (2022) Disponível em: <https://www.kaggle.com/datasets/lfarhat/brasil-students-scholarship-prouni-20052019>. Acesso em: 18 jun. 2023.
- ProUni - Apresentação. (2018) Disponível em: <http://portal.mec.gov.br/prouni-sp-1364717183/apresentacao>. Acesso em: 18 jun. 2023.
- Visualização de Dados | Microsoft Power BI. (2023) Disponível em: <https://powerbi.microsoft.com/pt-br/>. Acesso em: 18 jun. 2023.
