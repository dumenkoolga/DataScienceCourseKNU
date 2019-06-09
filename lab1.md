# Лабораторна робота № 1

## 1. Створити змінні базових (atomic) типів. Базові типи: character, numeric, integer, complex, logical.

```{R}
a <- "word" #character
print(a) 
[1] "word"

b <- 22 #numeric 
print(b)
[1] 22

c <- 5733L #integer
print (c)
[1] 5733

d <- 2+8i #complex
print (d)
[1] 2+8i

e <- F #logic 
print (e)
[1] FALSE
```

## 2. Створити вектори, які: містить послідовність з 5 до 75; містить числа 3.14, 2.71, 0, 13; 100 значень TRUE.

```{R}
v1<-(5:75) #integer
print (v1)
[1]  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
[22] 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46
[43] 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67
[64] 68 69 70 71 72 73 74 75

v2<-c(3.14, 2.71, 0, 13) #numeric
print (v2)
[1]  3.14  2.71  0.00 13.00

v3<-rep(TRUE,100) #logical
print (v3)
  [1] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [13] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [25] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [37] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [49] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [61] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [73] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [85] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
 [97] TRUE TRUE TRUE TRUE
```

## 3.Створити наступну матрицю за допомогою matrix, та за допомогою cbind або rbind 0.5 1.3 3.5 3.9 131 2.8 0 2.2 4.6 2 7 5.1

```{R}
matrix1 <- matrix(c(0.5, 3.9, 0, 2, 1.3, 131, 2.2, 7, 3.5, 2.8, 4.6, 5.1), nrow = 4, ncol = 3) #1st method
print(matrix1)
     [,1]  [,2] [,3]
[1,]  0.5   1.3  3.5
[2,]  3.9 131.0  2.8
[3,]  0.0   2.2  4.6
[4,]  2.0   7.0  5.1

var1 <- c(0.5, 3.9, 0, 2) 
var2 <- c(1.3, 131, 2.2, 7)
var3 <- c(3.5, 2.8, 4.6, 5.1)
cbind(var1, var2, var3) #2nd method
     var1  var2 var3
[1,]  0.5   1.3  3.5
[2,]  3.9 131.0  2.8
[3,]  0.0   2.2  4.6
[4,]  2.0   7.0  5.1

obs1<-c(0.5, 1.3, 3.5)
obs2<-c(3.9, 131, 2.8)
obs3<-c(0, 2.2, 4.6)
obs4<-c(2, 7, 5.1)
rbind(obs1,obs2,obs3,obs4) #3rd method
     [,1]  [,2] [,3]
obs1  0.5   1.3  3.5
obs2  3.9 131.0  2.8
obs3  0.0   2.2  4.6
obs4  2.0   7.0  5.1
```

## 4.Створити довільний список (list), в який включити всі базові типи.

```{R}
list_basic <- list(a, b, c, d, e)
print (list_basic)
[[1]]
[1] "word"

[[2]]
[1] 22

[[3]]
[1] 5733

[[4]]
[1] 2+8i

[[5]]
[1] FALSE
```

## 5.Створити фактор з трьома рівнями «baby», «child», «adult».

```{R}
demog <- factor(c("adult", "child", "baby", "adult"),
      levels=c("baby", "child", "adult"))
print(demog)
[1] adult child baby  adult
Levels: baby child adult
```

## 6.Знайти індекс першого значення NA в векторі 1, 2, 3, 4, NA, 6, 7, NA, 9, NA, 11. Знайти кількість значень NA.

```{R}
na_vector<-c(1,2,3,4,NA,6,7,NA,9,NA,11)
match(NA,na_vector)
[1] 5
sum(is.na(na_vector))
[1] 3
```

## 7. Створити довільний data frame та вивести в консоль.

```{R}
drug<-data.frame(patient=c(10100, 10101, 10102, 10103), 
      pills=c( "treatment", "placebo","placebo", "treatment"), tablets=c(1,0,0,2))
print (drug)
  patient     pills tablets
1   10100 treatment       1
2   10101   placebo       0
3   10102   placebo       0
4   10103 treatment       2
```

## 8. Змінити імена стовпців цього data frame.

```{R}
colnames(drug) <- c("SUBJID", "DRUG", "DOSE")
drug
  SUBJID      DRUG DOSE
1  10100 treatment    1
2  10101   placebo    0
3  10102   placebo    0
4  10103 treatment    2
```
