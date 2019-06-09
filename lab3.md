# Лабораторна робота № 3

## 1. Функція add2(x, y), яка повертає суму двох чисел.

```{R}
add2 <- function(x,y) 
        {
          x+y
        }
add2(5816.34,1819.4)
[1] 7635.74
```

## 2. Функція above(x, n), яка приймає вектор та число n, та повертає всі елементі вектору, які більше n. По замовчуванню n = 10.

```{R}
above<- function(x,n=10) 
        {
          x1=x[x>n]
          return(x1)
        }

above(test<-c(50, 5, 78, 9, 3, 11, 10))
[1] 50 78 11
```

## 3. Функція my_ifelse(x, exp, n), яка приймає вектор x, порівнює всі його елементи за допомогою exp з n, та повертає елементи вектору, які відповідають умові expression. Наприклад, my_ifelse(x, “>”, 0) повертає всі елементи x, які більші 0. Exp може дорівнювати “<”, “>”, “<=”, “>=”, “==”. Якщо exp не співпадає ні з одним з цих виразів, повертається вектор x.

```{R}
my_ifelse <- function(x, exp, n) 
            { 
                  if (exp == "<")        {
                            X1=x[x<n] 
                  } else if(exp == "<=") {
                            X1=x[x<=n]
                  } else if(exp == ">")  {
                            X1=x[x>n]
                  } else if(exp == ">=") {
                            X1=x[x>=n]
                  } else if(exp == "==") {
                            X1=x[x==n]
                  } else { 
                            X1=x
                         }
                  return(X1)
            }
                  
my_ifelse(test,"<",20) 
[1]  5  9  3 11 10

my_ifelse(test,"=<=",18) 
[1] 50  5 78  9  3 11 10

my_ifelse(test,">=",60) 
[1] 78

my_ifelse(test,"==",0) 
numeric(0)
```

## 4. Функція columnmean(x, removeNA), яка розраховує середнє значення (mean) по кожному стовпцю матриці, або data frame. Логічний параметр removeNA вказує, чи видаляти NA значення. По замовчуванню він дорівнює TRUE.

```{R}
columnmean<- function(x, removeNA=TRUE) 
            {
             apply(x,2,mean, na.rm = removeNA) # applies function 'mean' to 2nd dimension (columns)
            }
             
matrix1 <- matrix(c(0.5, 3.9, NA, 2, 1.3, NA, 2.2, 7, 3.5, 2.8, 4.6, 4.1), nrow = 4, ncol = 3)
matrix1
     [,1] [,2] [,3]
[1,]  0.5  1.3  3.5
[2,]  3.9   NA  2.8
[3,]   NA  2.2  4.6
[4,]  2.0  7.0  4.1

columnmean(matrix1)
[1] 2.133333 3.500000 3.750000

columnmean(matrix1,removeNA=FALSE)
[1]   NA   NA 3.75
```

