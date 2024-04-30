# Tarea_calificada2
#Tarea
import pandas as pd
LINK_tarea='https://docs.google.com/spreadsheets/d/e/2PACX-1vSPVJIoDhupNyUpYD65FSHt6kMmF_KaxE2RD6CV1FOMP4vVw7WfKQMqpqo0ieD9vhMAmYP1NpBmw0od/pub?gid=658985149&single=true&output=csv'
data_tarea=pd.read_csv(LINK_tarea)
data_tarea
#Borrar las letras de las columnas 6,8,10, 12 y 14 unnamed 5 7 9 11 13
data_tarea[['Unnamed: 5','Unnamed: 7','Unnamed: 9','Unnamed: 11','Unnamed: 13']]=data_tarea[['Unnamed: 5','Unnamed: 7','Unnamed: 9','Unnamed: 11','Unnamed: 13']].replace('[a-zA-Z,]','',regex=True)
#Borra las comas de la columna 10
data_tarea['Unnamed: 10'] = data_tarea['Unnamed: 10'].astype(str).str.replace(',', '')
#Reemplaza los nombres de las columnas
data_tarea.columns = data_tarea.iloc[3]
data_tarea.columns.values[1] = 'Country'
data_tarea=data_tarea.drop(data_tarea.index[:5]).reset_index(drop=True)
#Elimina las columnas que no correspondan
data_tarea.columns.to_list()
data_tarea=data_tarea.iloc[:,[1,3,4,6,7,8,9,10,11,12,13,14]]
data_tarea = data_tarea.drop(data_tarea.columns[[1,3,6]], axis=1)
