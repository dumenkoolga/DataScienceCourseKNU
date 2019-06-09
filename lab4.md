# Лабораторна робота № 4

## 1. Які назви стовпців файлу даних?

```{R}
weather = read.csv("hw1_data.csv")
colnames(weather)
```
## 2. Які назви стовпців файлу даних?

```{R}
head(weather, 6)
```

## 3. Які назви стовпців файлу даних?

```{R}
nrow(weather)
```
## 4. Виведіть останні 10 строк дата фрейму.

```{R}
tail(weather, 10)
```
## 5. Як багато значень «NA» в стовпці «Ozone»?
```{R}
sum(is.na(weather$Ozone))
```
## 6. Яке середнє (mean) стовпця «Ozone». Виключити «NA» значення.

```{R}
mean(weather$Ozone, na.rm = TRUE)  
```

## 7. Виведіть частину набору даних (subset) зі значенням «Ozone» > 31 та «Temp» > 90. Яке середнє (mean) значень «Solar.R» в цьому наборі даних (subset)?

```{R}
hot<-subset(weather, Ozone>31 & Temp>90)
hot 

mean(hot$Solar.R, na.rm=T)
```

## 8. Яке середнє значення (mean) для «Temp» для червня («Month» дорівнює 6)?

```{R}
june<-subset(weather, Month==6)
mean(june$Temp,na.rm=T) 
```

## 9. Яке максимальне значення «Ozone» для травня («Month» дорівнює 5)?
```{R}
may<-subset(weather, Month==5)
max(may$Ozone,na.rm=T) 
```
