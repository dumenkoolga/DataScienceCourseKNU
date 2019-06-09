# Лабораторна робота № 1

## 1. Створити змінні базових (atomic) типів. Базові типи: character, numeric, integer, complex, logical.

```{R}
a <- "word" #character
print(a) 

b <- 22 #numeric 
print(b)

c <- 5733L #integer
print (c)

d <- 2+8i #complex
print (d)

e <- F #logic 
print (e)
```

## 2. Створити вектори, які: містить послідовність з 5 до 75; містить числа 3.14, 2.71, 0, 13; 100 значень TRUE.

```{R}
v1<-(5:75) #integer
print (v1)

v2<-c(3.14, 2.71, 0, 13) #numeric
print (v2)

v3<-rep(TRUE,100) #logical
print (v3)
```

## 3.Створити наступну матрицю за допомогою matrix, та за допомогою cbind або rbind 0.5 1.3 3.5 3.9 131 2.8 0 2.2 4.6 2 7 5.1

```{R}
matrix1 <- matrix(c(0.5, 3.9, 0, 2, 1.3, 131, 2.2, 7, 3.5, 2.8, 4.6, 5.1), nrow = 4, ncol = 3) #1st method
print(matrix1)

var1 <- c(0.5, 3.9, 0, 2) 
var2 <- c(1.3, 131, 2.2, 7)
var3 <- c(3.5, 2.8, 4.6, 5.1)
cbind(var1, var2, var3) #2nd method

obs1<-c(0.5, 1.3, 3.5)
obs2<-c(3.9, 131, 2.8)
obs3<-c(0, 2.2, 4.6)
obs4<-c(2, 7, 5.1)
rbind(obs1,obs2,obs3,obs4) #3rd method
```

## 4.Створити довільний список (list), в який включити всі базові типи.

```{R}
list_basic <- list(a, b, c, d, e)
print (list_basic)
```

## 5.Створити фактор з трьома рівнями «baby», «child», «adult».

```{R}
demog <- factor(c("adult", "child", "baby", "adult"),
      levels=c("baby", "child", "adult"))
print(demog)
```

## 6.Знайти індекс першого значення NA в векторі 1, 2, 3, 4, NA, 6, 7, NA, 9, NA, 11. Знайти кількість значень NA.

```{R}
na_vector<-c(1,2,3,4,NA,6,7,NA,9,NA,11)
match(NA,na_vector)
sum(is.na(na_vector))
```

## 7. Створити довільний data frame та вивести в консоль.

```{R}
drug<-data.frame(patient=c(10100, 10101, 10102, 10103), pills=c( "treatment", "placebo","placebo", "treatment"), tablets=c(1,0,0,2))
print (drug)

```

## 8. Змінити імена стовпців цього data frame.

```{R}
colnames(drug) <- c("SUBJID", "DRUG", "DOSE")
drug

```
