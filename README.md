# Repaso-antes-del-Final
Repaso antes del final 


```{r}
library(rio)
library(dplyr)
library(psych)
library(dplyr)
library(cluster)
```

```{r}
Data = import("Planeamiento_estratégico.xlsx")
```

```{r}
Data <- Data %>% 
  filter(Estrato == "Provincia")
```

```{r}
cols_a_convertir <- c("Bajo_Peso", "Desnutricion", "Anemia", "IVIA", "IDE", "IDH", "Devengado_Act", "Devengado_Inv")
```


```{r}
Data_Limpia <- Data %>% 
  filter(Estrato == "Provincia") %>% 
  
  select(
    Ubigeo,
    Provincia = contains("Región"), # Aquí se crea la columna 'Provincia'
    Bajo_Peso = contains("bajo peso al nacer"),
    Desnutricion = starts_with("Desnutrición"),
    Anemia = starts_with("Anemia"),
    IVIA = contains("Inseguridad Alimentaria"),
    IDE = contains("Densidad del Estado"),
    IDH = matches("^IDH"), 
    Devengado_Act = contains("Actividad"),
    Devengado_Inv = contains("Inversión")
  ) 
```
```{r}

export(Data_Limpia, "Data_CEPLAN_Limpia.csv")

str(Data_Limpia)
```
