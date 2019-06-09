# Лабораторна робота № 7

## 1. Напишіть функцію prepare_set <- function(file_name) {} яка в якості аргументу приймає ім’я файлу і повертає дата фрейм. Збережіть цей дата фрейм в змінну

```{R}
prepare_set <- function() {
df <- read.csv("olympics.csv", skip = 1, header = TRUE, encoding="UTF-8", stringsAsFactors = FALSE)
names(df)

names(df)[1] = "Country"

   for (i in 1:length(names(df))) {
    name <- names(df)[i]
    if (str_sub(name, 2, 3) == "01") names(df)[i] <- str_c("Gold", str_sub(name, 6))
    if (str_sub(name, 2, 3) == "02") names(df)[i] <- str_c("Silver", str_sub(name, 6))
    if (str_sub(name, 2, 3) == "03") names(df)[i] <- str_c("Bronze", str_sub(name, 6))
    if (str_sub(name, 3, 3) == "U") names(df)[i] <- str_sub(name, 11)
   }
   
   prepare_set()
```
