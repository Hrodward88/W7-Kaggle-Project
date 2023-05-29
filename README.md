# W7-Kaggle-Project

Predicción de precio de ordenadores

Partiendo del siguiente dataframe, 'Training':

RangeIndex: 977 entries, 0 to 976
Data columns (total 13 columns):
 #   Column                    Non-Null Count  Dtype  
---  ------                    --------------  -----  
 0   Manufacturer              977 non-null    object 
 1   Model Name                977 non-null    object 
 2   Category                  977 non-null    object 
 3   Screen Size               977 non-null    object 
 4   Screen                    977 non-null    object 
 5   CPU                       977 non-null    object 
 6   RAM                       977 non-null    object 
 7    Storage                  977 non-null    object 
 8   GPU                       977 non-null    object 
 9   Operating System          977 non-null    object 
 10  Operating System Version  841 non-null    object 
 11  Weight                    977 non-null    object 
 12  Price                     977 non-null    float64
dtypes: float64(1), object(12)

Lo primero que se hiz fue comprobar la variedad de valores distintos en cada una de las columnas, y comprobar cuáles pueden convertirse en columnas numéricas.

Mediante LabelEncoder, cree nuevas columnas con valores numéricos para Manufacturer, Category, Sceen, SPU, Storage y GPU.

Mediante una función llamada 'get_numeric' 

def convert_to_numeric(strings):
    result = []
    for string in strings:
        numeric_value = re.findall(r'\d+\.?\d*', string)
        if numeric_value:
            result.append(pd.to_numeric(numeric_value[0]))
    return result
    
Se limpian y convierten en numérico las columnas RAM, Screen Size, y Weight.
    
Con todas estas columnas numéricas, podemos realizar una matriz de correlación y ver que elementos tienen mayor impacto, y cuales tienen alta colinealida, como Screen Size y Weight.

Finalmente, tenemos 3 categorís principales que influyen en el precio: CPU, RAM, Storage, y GPU.

Guardamos eso como un nuevo archivo .csv, y lo usamos para entrenar el modelo.
    
