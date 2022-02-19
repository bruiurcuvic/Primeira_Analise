# Primeira_Analise
Essa analise é simples, e tem como objetivo apenas a implementação da aprendizagem em aulas.

O estudo se trata da analise de duas escolas situadas em Portugal.

# Importando os pacotes
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import plotly.express as px


# Lendo os dados
mat2= pd.read_csv('/content/student-mat.csv', sep=';')
port1= pd.read_csv('/content/student-por.csv', sep=';')

# Limpando, tratando e minerando os dados
# Matematica: 
mat2= mat2.rename(columns={'school':'Escola','sex':'Sexo','age':'Idade','address':'Tipo_Moradia','Pstatus':'Relação_Pais','Medu':'Educação_mae',
                          'Fedu':'Educação_pai','Mjob':'Trabalho_mae','Fjob':'Trabalho_pai','reason':'Motivo_escolha','guardian':'Guardião',
                          'studytime':'Tempo_estudo','schoolsup':'Apoio_extra','famsup':'Apoio_familia','paid':'AulaExtra_paga',
                          'activities':'Atividade_extra','higher':'Pretende_ensinoSuperior','romantic':'Possui_relacionamento','famrel':'NivelRelacFamilia',	
                          'Dalc':'Consumo_alcool','health':'Saude_mental'})
mat2= mat2.rename(columns={'absences':'Numero_faltas'})
mat2= mat2.drop(columns=['famsize','traveltime','nursery','freetime','goout','Walc'], )
mat2["Tipo_Moradia"]= mat2["Tipo_Moradia"].replace({'U':"Urbano", 'R':"Rural"})
mat2["Relação_Pais"]= mat2["Relação_Pais"].replace({'T':"Juntos", 'A':"Separados"})
mat2["Educação_mae"]= mat2["Educação_mae"].replace({0:"N/T", 1:"Fundamental", 2:'5 ao 9',3:'Médio',4:'Superior'})
mat2["Educação_pai"]= mat2["Educação_pai"].replace({0:"N/T", 1:"Fundamental", 2:'5 ao 9',3:'Médio',4:'Superior'})
mat2["Guardião"]= mat2["Guardião"].replace({'mother':"mãe", 'father':"pai",'other':'outro'})
mat2["NivelRelacFamilia"]= mat2["NivelRelacFamilia"].replace({1:'muitoRuim', 2:"Ruim", 3:'Satisfatorio',4:'bom',5:'MuitoBom'})
mat2["Tempo_estudo"]= mat2["Tempo_estudo"].replace({1:'<2 horas', 2:"2 a 5 horas", 3:'5 a 10 horas',4:'>10 horas'})
mat2["Consumo_alcool"]= mat2["Consumo_alcool"].replace({1:'muitoBaixo', 2:"baixo", 3:'Razoavel',4:'Alto',5:'MuitoAlto'})
mat2["Saude_mental"]= mat2["Saude_mental"].replace({1:'muitoRuim', 2:"Ruim", 3:'Satisfatorio',4:'bom',5:'MuitoBom

# Português: 
port1= port1.rename(columns={'school':'Escola','sex':'Sexo','age':'Idade','address':'Tipo_Moradia','Pstatus':'Relação_Pais','Medu':'Educação_mae',
                          'Fedu':'Educação_pai','Mjob':'Trabalho_mae','Fjob':'Trabalho_pai','reason':'Motivo_escolha','guardian':'Guardião',
                          'studytime':'Tempo_estudo','schoolsup':'Apoio_extra','famsup':'Apoio_familia','paid':'AulaExtra_paga',
                          'activities':'Atividade_extra','higher':'Pretende_ensinoSuperior','romantic':'Possui_relacionamento','famrel':'NivelRelacFamilia',	
                          'Dalc':'Consumo_alcool','health':'Saude_mental'})
port1= port1.rename(columns={'absences':'Numero_faltas'})
port1= port1.drop(columns=['famsize','traveltime','nursery','freetime','goout','Walc'], )
port1= port1.drop(columns=['failures'], )
port1["Tipo_Moradia"]= port1["Tipo_Moradia"].replace({'U':"Urbano", 'R':"Rural"})
port1["Relação_Pais"]= port1["Relação_Pais"].replace({'T':"Juntos", 'A':"Separados"})
port1["Educação_mae"]= port1["Educação_mae"].replace({0:"N/T", 1:"Fundamental", 2:'5 ao 9',3:'Médio',4:'Superior'})
port1["Educação_pai"]= port1["Educação_pai"].replace({0:"N/T", 1:"Fundamental", 2:'5 ao 9',3:'Médio',4:'Superior'})
port1["Guardião"]= port1["Guardião"].replace({'mother':"mãe", 'father':"pai",'other':'outro'})
port1["NivelRelacFamilia"]= port1["NivelRelacFamilia"].replace({1:'muitoRuim', 2:"Ruim", 3:'Satisfatorio',4:'bom',5:'MuitoBom'})
port1["Tempo_estudo"]= port1["Tempo_estudo"].replace({1:'<2 horas', 2:"2 a 5 horas", 3:'5 a 10 horas',4:'>10 horas'})
port1["Consumo_alcool"]= port1["Consumo_alcool"].replace({1:'muitoBaixo', 2:"baixo", 3:'Razoavel',4:'Alto',5:'MuitoAlto'})
port1["Saude_mental"]= port1["Saude_mental"].replace({1:'muitoRuim', 2:"Ruim", 3:'Satisfatorio',4:'bom',5:'MuitoBom'})


# Verificando valores nulos.
* Matematica
mat2.isnull().sum()
* Português
port1.isnull().sum()
