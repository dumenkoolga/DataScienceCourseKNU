# Лабораторна робота № 7

## 1. Напишіть функцію prepare_set <- function(file_name) {} яка в якості аргументу приймає ім’я файлу і повертає дата фрейм. Збережіть цей дата фрейм в змінну

library(stringr)

```{R}
prepare_set <- function(file_name) {
  df <- read.csv(file_name, skip = 1, header = TRUE, encoding="UTF-8", stringsAsFactors = FALSE)
  names(df)
  
  colnames(df)[1] <- "Country" 
  for (i in 1:length(names(df))) {
    name <- names(df)[i]
    if (str_sub(name, 2, 3) == "01") names(df)[i] <- str_c("Gold", str_sub(name, 6))
    if (str_sub(name, 2, 3) == "02") names(df)[i] <- str_c("Silver", str_sub(name, 6))
    if (str_sub(name, 2, 3) == "03") names(df)[i] <- str_c("Bronze", str_sub(name, 6))
    if (str_sub(name, 3, 3) == "U") names(df)[i] <- str_sub(name, 11)
  }
  df$Country <- as.character(df$Country)
  new_countr <- strsplit(df$Country, "(", fixed=TRUE)
  df$Country <- sapply(new_countr, "[", 1)
  df$Country <- str_trim(df$Country)
  df$ID <- sapply(new_countr, "[", 2)
  df$ID <- str_sub(df$ID, 1, 3)
  df <- subset(df, df$Country!="Totals")
  df
}
```
## Результати
```{R}
olympics <- prepare_set("olympics.csv")

answer_one = function(){
  olympics[which.max(olympics$Gold), "Country"]
}
answer_two = function(){
  olympics[which.max(olympics$Total-olympics$Total.1), "Country"]
}
answer_three = function(){
  morethanone = subset(olympics, Total >0 & Total.1 >0)
  morethanone[which.max((olympics$Gold-olympics$Gold.1)/olympics$Gold.2), "Country"]
}
answer_four = function(){
  olympics$Score = (olympics$Gold.2*3+olympics$Silver.2*2 +olympics$Bronze.2)
  df <- data.frame(olympics$Country,  olympics$Score)
  names(df) <- c('Country', 'Score')
  df
  
}

answer_one()

answer_two()

answer_three()

answer_four()


```

## Частина 2
```{R}
cs <- read.csv("census.csv", stringsAsFactors = FALSE)

answer_five<-function() {
  cs_gr <- split(cs, cs$STNAME)
  c_per_st <- sapply(cs_gr, nrow)
  max_state <- names(which.max(c_per_st))
  max_state
}


answer_six<-function() {
  cs_ord<-cs[order(cs$STNAME, -cs$CENSUS2010POP), ]
  cs_gr <- split(cs_ord, cs$STNAME)
  cs_gr<-lapply(cs_gr, function (x) sum (x[2:4, "CENSUS2010POP"]))
  cs_gr<-cs_gr[order(unlist(cs_gr), decreasing = TRUE, na.last = TRUE)]
  state_list <- names(cs_gr)[1:3]
  state_list
}

answer_seven<-function() {
  cs_subs<-cs[, 10:15]
  max_cs_subs<-apply(cs_subs, 1, max)
  min_cs_subs<-apply(cs_subs, 1, min)
  delta_cs<-abs(max_cs_subs-min_cs_subs)
  cs_res<-cbind(CTYNAME = cs$CTYNAME, delta_cs)
  cs_res[which.max(delta_cs)]
}

answer_eight <- function() {
  cs_reg<-subset(cs, (REGION==1 & REGION==2))
  cs_wsh<-cs_reg[startsWith("Washington",cs_reg$CTYNAME),]
  cs_15<-subset(cs_wsh, cs_wsh$POPESTIMATE2015 > cs_wsh$POPESTIMATE2014)
  cs_final <- cs_15[ , c("STNAME", "CTYNAME")]
  cs_final
}

answer_five()
answer_six()
answer_seven()
answer_eight()

```
