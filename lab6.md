# Лабораторна робота № 6

## 1. Створити матрицю mat з 5 стовпцями та 10 строками за допомогою matrix з випадковими даними (функція rnorm(50)).

```{R}
mat <- matrix(rnorm(50),nrow = 10, ncol = 5)    
mat
```

## 2. Знайти максимальне значення в кожному стовпці.

```{R}
apply(mat, 2, max)
```

## 3. Знайти середнє (mean) значення кожного стовпця.

```{R}
apply(mat, 2, mean)
```
## 4. Знайти мінімальне значення в кожному рядку.

```{R}
apply(mat, 1, min)
```

## 5. Відсортувати кожен стовбець таблиці.

```{R}
apply(mat, 2, sort) 
```

## 6. Знайти кількість значень < 0 для кожного стовпця. Використати свою функцію.

```{R}
less_zero <-function(x) { sum(x<0) }
apply(mat, 2, less_zero)

```

## 7. Вивести вектор з булевими значеннями TRUE та FALSE. TRUE, якщо в стовпці є елементи >2, FALSE – якщо немає.

```{R}
more_two <-function(x) { sum(x>2)>0 }
apply(mat,2,more_two)
```

## 8. Створить список list1 <- list(observationA = c(1:5, 7:3), observationB = matrix(1:6, nrow=2)). Для цього списку знайдіть sum за допомогою lapply.

```{R}
list1 <- list(observationA = c(1:5, 7:3), observationB = matrix(1:6, nrow=2))
list1

lapply(list1, sum)
```
## 9. Для кожного елементу списку list1 знайдіть максимальне та мінімальне значення (range) за допомогою lapply та sapply.

```{R}
lapply(list1, range)

sapply(list1, range)
```

## 10. Для вбудованого набору даних InsectSprays знайти середнє count для кожного spray.

```{R}
spray <- split(InsectSprays$count, InsectSprays$spray)

lapply(spray, mean)

sapply(spray, mean)
```




