# Лабораторна робота № 2

## 1. Створить вектор v із 100 елементів командою v <- rnorm(100). Для цього вектору виведіть: 10-й елемент; елементи з 10-го по 20-й включно; 10 елементів починаючи з 20-го; елементи більше 0.

```{R}
v<-rnorm(100)
v

v[10] #10th element

v[10:20] #from 10th to 20th elements

v[20:29] #10 elements from 20th

v[v > 0] #positive values

```

## 2. Створити фрейм (data frame) y командою y <- data.frame(a = rnorm(100), b = 1:100, cc = sample(letters, 100, replace = TRUE)). Для цього data frame виведіть: останні 10 строк; строки з 10 по 20 включно; 10-й елемент стовпця b; повністю стовпець cc, при цьому використайте ім’я стовпця.

```{R}
y <- data.frame(a = rnorm(100), b = 1:100, cc = sample(letters, 100, replace = TRUE))
y

tail(y, 10) #last 10 rows

y[c(10:20), ] #from 10 to 20 row

y[10, "b"] #10th element from b column

y[["cc"]] 
```

## 3. Створити вектор z з елементами 1, 2, 3, NA, 4, NA, 5, NA. Для цього вектору: виведіть всі елементи, які не NA; підрахуйте середнє значення всіх елементів цього вектору без NA значень та з NA значеннями.

```{R}
z<-c(1, 2, 3, NA, 4, NA, 5, NA)
z
 
nonmiss_z <- is.na(z)
z[!nonmiss_z]

mean(z[!nonmiss_z])

mean(z)
 ```