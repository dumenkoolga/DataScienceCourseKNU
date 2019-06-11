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
[1] "United States"

answer_two()
[1] "United States"

answer_three()
[1] "Austria"
 answer_four()
                             Country Score
1                        Afghanistan     2
2                            Algeria    27
3                          Argentina   130
4                            Armenia    16
5                        Australasia    22
6                          Australia   923
7                            Austria   569
8                         Azerbaijan    43
9                            Bahamas    24
10                           Bahrain     1
11                          Barbados     1
12                           Belarus   154
13                           Belgium   276
14                           Bermuda     1
15                           Bohemia     5
16                          Botswana     2
17                            Brazil   184
18               British West Indies     2
19                          Bulgaria   411
20                           Burundi     3
21                          Cameroon    12
22                            Canada   846
23                             Chile    24
24                             China  1120
25                          Colombia    29
26                        Costa Rica     7
27                       Ivory Coast     2
28                           Croatia    67
29                              Cuba   420
30                            Cyprus     2
31                    Czech Republic   134
32                    Czechoslovakia   327
33                           Denmark   335
34                          Djibouti     1
35                Dominican Republic    14
36                           Ecuador     5
37                             Egypt    49
38                           Eritrea     1
39                           Estonia    77
40                          Ethiopia    94
41                           Finland   895
42                            France  1500
43                             Gabon     2
44                           Georgia    42
45                           Germany  1546
46            United Team of Germany   269
47                      East Germany  1068
48                      West Germany   459
49                             Ghana     5
50                     Great Britain  1574
51                            Greece   213
52                           Grenada     3
53                         Guatemala     2
54                            Guyana     1
55                             Haiti     3
56                         Hong Kong     6
57                           Hungary   962
58                           Iceland     6
59                             India    50
60                         Indonesia    49
61                              Iran   110
62                              Iraq     1
63                           Ireland    55
64                            Israel    10
65                             Italy  1333
66                           Jamaica   131
67                             Japan   866
68                        Kazakhstan   113
69                             Kenya   168
70                       North Korea    90
71                       South Korea   609
72                            Kuwait     2
73                        Kyrgyzstan     4
74                            Latvia    47
75                           Lebanon     6
76                     Liechtenstein    15
77                         Lithuania    38
78                        Luxembourg     9
79                         Macedonia     1
80                          Malaysia     9
81                         Mauritius     1
82                            Mexico   109
83                           Moldova     9
84                          Mongolia    37
85                        Montenegro     2
86                           Morocco    39
87                        Mozambique     4
88                           Namibia     8
89                       Netherlands   727
90              Netherlands Antilles     2
91                       New Zealand   203
92                             Niger     1
93                           Nigeria    37
94                            Norway   985
95                          Pakistan    19
96                            Panama     5
97                          Paraguay     2
98                              Peru     9
99                       Philippines    11
100                           Poland   520
101                         Portugal    39
102                      Puerto Rico    10
103                            Qatar     4
104                          Romania   572
105                           Russia  1042
106                   Russian Empire    14
107                     Soviet Union  2526
108                     Unified Team   287
109                     Saudi Arabia     4
110                          Senegal     2
111                           Serbia    11
112            Serbia and Montenegro    17
113                        Singapore     6
114                         Slovakia    58
115                         Slovenia    56
116                     South Africa   148
117                            Spain   268
118                        Sri Lanka     4
119                            Sudan     2
120                         Suriname     4
121                           Sweden  1217
122                      Switzerland   630
123                            Syria     6
124                   Chinese Taipei    32
125                       Tajikistan     4
126                         Tanzania     4
127                         Thailand    44
128                             Togo     1
129                            Tonga     2
130              Trinidad and Tobago    27
131                          Tunisia    19
132                           Turkey   191
133                           Uganda    14
134                          Ukraine   220
135             United Arab Emirates     3
136                    United States  5684
137                          Uruguay    16
138                       Uzbekistan    38
139                        Venezuela    18
140                          Vietnam     4
141                   Virgin Islands     2
142                       Yugoslavia   171
143 Independent Olympic Participants     4
144                           Zambia     3
145                         Zimbabwe    18
146                       Mixed team    38

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
[1] "Texas"
answer_six()
[1] "California" "Texas"      "Illinois" 
answer_seven()
[1] "Texas"
answer_eight()
          STNAME           CTYNAME
897          Iowa Washington County
1420    Minnesota Washington County
2346 Pennsylvania Washington County
2356 Rhode Island Washington County
3164    Wisconsin Washington County

```
