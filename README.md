# Primeira_Analise
Essa analise é simples, e tem como objetivo apenas a implementação da aprendizagem em aulas.

O estudo se trata da analise de duas escolas situadas em Portugal. A analise foi separada por materia e logo em seguida por escola. Levando em consideração,
que em ambas os alunos optão por apenas uma das materias, e alunos que escolheram as duas foram descartados da base de dados.
* Legenda: G1- Notas do primeiro perioso, G2- Notas do segundo perioso, G3- Notas do terceiro periodo, GP e MS - Abreviação dos nomes das escolas.

# Importando os pacotes:
* import pandas as pd
* import numpy as np
* import seaborn as sns
* import matplotlib.pyplot as plt
* import plotly.express as px


# Lendo os dados
* mat2= pd.read_csv('/content/student-mat.csv', sep=';')
* port1= pd.read_csv('/content/student-por.csv', sep=';')

# Limpando, tratando e minerando os dados
# Matematica: 
* mat2= mat2.rename(columns={'school':'Escola','sex':'Sexo','age':'Idade','address':'Tipo_Moradia','Pstatus':'Relação_Pais','Medu':'Educação_mae',
                          'Fedu':'Educação_pai','Mjob':'Trabalho_mae','Fjob':'Trabalho_pai','reason':'Motivo_escolha','guardian':'Guardião',
                          'studytime':'Tempo_estudo','schoolsup':'Apoio_extra','famsup':'Apoio_familia','paid':'AulaExtra_paga',
                          'activities':'Atividade_extra','higher':'Pretende_ensinoSuperior','romantic':'Possui_relacionamento','famrel':'NivelRelacFamilia',	
                          'Dalc':'Consumo_alcool','health':'Saude_mental'})
* mat2= mat2.rename(columns={'absences':'Numero_faltas'})
* mat2= mat2.drop(columns=['famsize','traveltime','nursery','freetime','goout','Walc'], )
* mat2["Tipo_Moradia"]= mat2["Tipo_Moradia"].replace({'U':"Urbano", 'R':"Rural"})
* mat2["Relação_Pais"]= mat2["Relação_Pais"].replace({'T':"Juntos", 'A':"Separados"})
* mat2["Educação_mae"]= mat2["Educação_mae"].replace({0:"N/T", 1:"Fundamental", 2:'5 ao 9',3:'Médio',4:'Superior'})
* mat2["Educação_pai"]= mat2["Educação_pai"].replace({0:"N/T", 1:"Fundamental", 2:'5 ao 9',3:'Médio',4:'Superior'})
* mat2["Guardião"]= mat2["Guardião"].replace({'mother':"mãe", 'father':"pai",'other':'outro'})
* mat2["NivelRelacFamilia"]= mat2["NivelRelacFamilia"].replace({1:'muitoRuim', 2:"Ruim", 3:'Satisfatorio',4:'bom',5:'MuitoBom'})
* mat2["Tempo_estudo"]= mat2["Tempo_estudo"].replace({1:'<2 horas', 2:"2 a 5 horas", 3:'5 a 10 horas',4:'>10 horas'})
* mat2["Consumo_alcool"]= mat2["Consumo_alcool"].replace({1:'muitoBaixo', 2:"baixo", 3:'Razoavel',4:'Alto',5:'MuitoAlto'})
* mat2["Saude_mental"]= mat2["Saude_mental"].replace({1:'muitoRuim', 2:"Ruim", 3:'Satisfatorio',4:'bom',5:'MuitoBom

# Português: 
* port1= port1.rename(columns={'school':'Escola','sex':'Sexo','age':'Idade','address':'Tipo_Moradia','Pstatus':'Relação_Pais','Medu':'Educação_mae',
                          'Fedu':'Educação_pai','Mjob':'Trabalho_mae','Fjob':'Trabalho_pai','reason':'Motivo_escolha','guardian':'Guardião',
                          'studytime':'Tempo_estudo','schoolsup':'Apoio_extra','famsup':'Apoio_familia','paid':'AulaExtra_paga',
                          'activities':'Atividade_extra','higher':'Pretende_ensinoSuperior','romantic':'Possui_relacionamento','famrel':'NivelRelacFamilia',	
                          'Dalc':'Consumo_alcool','health':'Saude_mental'})
* port1= port1.rename(columns={'absences':'Numero_faltas'})
* port1= port1.drop(columns=['famsize','traveltime','nursery','freetime','goout','Walc'], )
* port1= port1.drop(columns=['failures'], )
* port1["Tipo_Moradia"]= port1["Tipo_Moradia"].replace({'U':"Urbano", 'R':"Rural"})
* port1["Relação_Pais"]= port1["Relação_Pais"].replace({'T':"Juntos", 'A':"Separados"})
* port1["Educação_mae"]= port1["Educação_mae"].replace({0:"N/T", 1:"Fundamental", 2:'5 ao 9',3:'Médio',4:'Superior'})
* port1["Educação_pai"]= port1["Educação_pai"].replace({0:"N/T", 1:"Fundamental", 2:'5 ao 9',3:'Médio',4:'Superior'})
* port1["Guardião"]= port1["Guardião"].replace({'mother':"mãe", 'father':"pai",'other':'outro'})
* port1["NivelRelacFamilia"]= port1["NivelRelacFamilia"].replace({1:'muitoRuim', 2:"Ruim", 3:'Satisfatorio',4:'bom',5:'MuitoBom'})
* port1["Tempo_estudo"]= port1["Tempo_estudo"].replace({1:'<2 horas', 2:"2 a 5 horas", 3:'5 a 10 horas',4:'>10 horas'})
* port1["Consumo_alcool"]= port1["Consumo_alcool"].replace({1:'muitoBaixo', 2:"baixo", 3:'Razoavel',4:'Alto',5:'MuitoAlto'})
* port1["Saude_mental"]= port1["Saude_mental"].replace({1:'muitoRuim', 2:"Ruim", 3:'Satisfatorio',4:'bom',5:'MuitoBom'})


# Verificando valores nulos.
Matematica: mat2.isnull().sum()
------------------------------------
* Escola                     0
* Sexo                       0
* Idade                      0
* Tipo_Moradia               0
* Relação_Pais               0
* Educação_mae               0
* Educação_pai               0
* Trabalho_mae               0
* Trabalho_pai               0
* Motivo_escolha             0
* Guardião                   0
* Tempo_estudo               0
* Apoio_extra                0
* Apoio_familia              0
* AulaExtra_paga             0
* Atividade_extra            0
* Pretende_ensinoSuperior    0
* internet                   0
* Possui_relacionamento      0
* NivelRelacFamilia          0
* Consumo_alcool             0
* Saude_mental               0
* Numero_faltas              0
* G1                         0
* G2                         0
* G3                         0
* dtype: int64
-----------------------------------



Português: port1.isnull().sum()
-----------------------------------

* Escola                     0
* Sexo                       0
* Idade                      0
* Tipo_Moradia               0
* Relação_Pais               0
* Educação_mae               0
* Educação_pai               0
* Trabalho_mae               0
* Trabalho_pai               0
* Motivo_escolha             0
* Guardião                   0
* Tempo_estudo               0
* Apoio_extra                0
* Apoio_familia              0
* AulaExtra_paga             0
* Atividade_extra            0
* Pretende_ensinoSuperior    0
* internet                   0
* Possui_relacionamento      0
* NivelRelacFamilia          0
* Consumo_alcool             0
* Saude_mental               0
* Numero_faltas              0
* G1                         0
* G2                         0
* G3                         0
* dtype: int64


# Verificando as medianas 

Matematica : mat2.mean()
--------------------------------
* Idade            16.696203
* Numero_faltas     5.708861
* G1               10.908861
* G2               10.713924
* G3               10.415190
* dtype: float64
--------------------------------

Português: port1.mean()
-------------------------------
* Idade            16.744222
* Numero_faltas     3.659476
* G1               11.399076
* G2               11.570108
* G3               11.906009

# Construções de graficos simples:
*Matematica vs Português: 
* sns.countplot( x = mat2['Escola']);

![download](https://user-images.githubusercontent.com/93952706/154822450-69b7741a-1b4b-4784-b0f7-66a46ba4f6e1.png)

*  sns.countplot( x = port1['Escola']);

![download](https://user-images.githubusercontent.com/93952706/154822485-46c51e0c-141a-40f1-8467-291d02a3827d.png)

* sns.countplot( x = mat2['NivelRelacFamilia']);

![download](https://user-images.githubusercontent.com/93952706/154822512-7a28e788-c8bc-4b2e-8385-dd512ee60508.png)

* sns.countplot( x = port1['NivelRelacFamilia']);

![download](https://user-images.githubusercontent.com/93952706/154822525-e205423a-5ef1-4ce5-8e56-ea57f5882825.png)

* sns.countplot( x = mat2['Tempo_estudo']);

![download](https://user-images.githubusercontent.com/93952706/154822569-6a4ac2d2-e86e-4285-ace1-7477a1a53479.png)

* sns.countplot( x = port1['Tempo_estudo']);

![download](https://user-images.githubusercontent.com/93952706/154822586-9a97c927-86f5-4063-a72b-dfacbbb359b1.png)

* sns.countplot( x = mat2['Sexo']);

![download](https://user-images.githubusercontent.com/93952706/154822631-e0d98615-4dae-42f9-ae61-31170ecb6f61.png)

* sns.countplot( x = port1['Sexo']);

![download](https://user-images.githubusercontent.com/93952706/154822640-e1e7d522-a6c8-41c4-bc19-cf3c8b08d855.png)

# Graficos aonde mostram maior volume de dados.

*Matematica vs Português

* plt.hist(x = mat2['Idade']);

![download](https://user-images.githubusercontent.com/93952706/154822664-a2d43d2a-65ef-45fb-8654-2e95fec06a75.png)

* plt.hist(x = port1['Idade']);

![download](https://user-images.githubusercontent.com/93952706/154822675-d57fc8e4-ef3e-45a4-96b7-eb87394d0e72.png)

# Amostragem por conglomerado(agrupamento)

*A analise a seguir, leva em consideração a separação por escola:

* Amostra para filtrar por escola

* tipo = mat2['Escola'].value_counts()
-----------------------------------------
* GP    349
* MS     46
* Name: Escola, dtype: int64
----------------------------------
* tipos = port1['Escola'].value_counts()
--------------------------------------------
* GP    423
* MS    226
* Name: Escola, dtype: int64

Em matematica, separando por escola, quantos alunos estudaram menos que duas horas
* escola = estudo['Escola'].value_counts()
---------------------------------------------------
* GP    89
* MS    16
* Name: Escola, dtype: int64
---------------------------------------------------
Em portugues, separando por escola, quantos alunos estudaram menos que duas horas
* escolas = estudos['Escola'].value_counts()
------------------------------------------------------
* GP    119
* MS     93
* Name: Escola, dtype: int64
------------------------------------------------------

Em matematica, separando por escola, quantos alunos são do sexo masculino
* esc = sexM['Escola'].value_counts()
------------------------------------------------------
* GP    166
* MS     21
* Name: Escola, dtype: int64
---------------------------------------------
Em matematica, separando por escola, quantos alunos são do sexo feminino
* esco = sexF['Escola'].value_counts()
------------------------------------------------------
* GP    183
* MS     25
* Name: Escola, dtype: int64
-----------------------------------------------------

Em portugues, separando por escola, quantos alunos são do sexo masculino
* escM = sexoM['Escola'].value_counts()
----------------------------------------------
* GP    186
* MS     80
* Name: Escola, dtype: int64
----------------------------------------------
Em portugues, separando por escola, quantos alunos são do sex feminino
* escF = sexoF['Escola'].value_counts()
--------------------------------------------
* GP    237
* MS    146
* Name: Escola, dtype: int64


*** Em processo ***
