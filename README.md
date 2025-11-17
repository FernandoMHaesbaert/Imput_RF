# Imputação de Dados Faltantes com Random Forest em R

A imputação de dados faltantes por meio do algoritmo Random Forest possibilita manter a distribuição dos dados.

Outras técnicas tradicionais são limitadas, como substituir pela média, mediana, etc.

**Procedimento**:   
- A imputação via Random Forest é realizada utiliando a função `missForest` do pacote {missForest}.  
- O missForest imputa valores ausentes para dados de tipos mistos (numéricos e categóricos).
- Ele modela interações complexas e relações não lineares e retorna uma estimativa de erro de imputação

**Exemplo:**
```{r}
library(missForest)
library(tidyverse)
set.seed(123)
df <- iris %>%
  mutate(across(where(is.numeric), ~ ifelse(runif(n()) < 0.1, NA, .)))
imputed <- missForest(df)
imputed$ximp |> 
  as_tibble()
```

**Referências**  
Stekhoven, D. J.; Bühlmann, P. **MissForest — nonparametric missing value imputation for mixed-type data.** *Bioinformatics*, 28(1), 112–118. 2012. <https://doi.org/10.1093/bioinformatics/btr597>.  
Salman, H. A.;  Kalakech, A.; Steiti, A. **Random Forest Algorithm Overview**. *Babylonian Journal of Machine Learning*, 2024, 69-79. 2024. <https://doi.org/10.58496/BJML/2024/007>.


**Acesse a página principal**: <https://fernandomhaesbaert.github.io/Imput_RF/>
