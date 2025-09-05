```r
library(readxl)
file.choose()

rota_dados <- "C:\\Users\\ingry\\Downloads\\dados - avengers.xlsx"

excel_sheets(rota_dados)
Dados <- read_excel(rota_dados)

#Brilheteria
mean(Dados$`Bilheteria bruta em todo o mundo`)
median(Dados$`Bilheteria bruta em todo o mundo`)
sum(Dados$`Bilheteria bruta em todo o mundo`)
var(Dados$`Bilheteria bruta em todo o mundo`)
sd(Dados$`Bilheteria bruta em todo o mundo`)

#correlação linear
cor(Dados$`Bilheteria bruta em todo o mundo`, Dados$Orçamento, method = "pearson")
cor(Dados$`Classificação do Rotten Tomatoes`, Dados$`Bilheteria bruta em todo o mundo`, method = "pearson")


#Classificação
mean(Dados$`Classificação do Rotten Tomatoes`)
median(Dados$`Classificação do Rotten Tomatoes`)
sum(Dados$`Classificação do Rotten Tomatoes`)
var(Dados$`Classificação do Rotten Tomatoes`)
sd(Dados$`Classificação do Rotten Tomatoes`)

#Orçamento
mean(Dados$Orçamento)
median(Dados$Orçamento)
sum(Dados$Orçamento)
var(Dados$Orçamento)
sd(Dados$Orçamento)

#DUração
mean(Dados$`Duração de filme`)
median(Dados$`Duração de filme`)
sum(Dados$`Duração de filme`)
var(Dados$`Duração de filme`)
sd(Dados$`Duração de filme`)

#gráficos
library(ggplot2)

ggplot(Dados, aes(x=`Bilheteria bruta em todo o mundo`, y=Orçamento))+
  geom_point(size = 2.2, colour = "purple")+
  labs(
    title = "Relação entre a Bilheteria e Orçamento",
    x = "Bilheteria mundial (em bilhões)",
    y = "Orçamento (em milhões)",
  )+
  theme_minimal()

ggplot(Dados, aes(x=`Classificação do Rotten Tomatoes`, y=`Bilheteria bruta em todo o mundo`))+
  geom_point(size = 2.2, colour = "purple")+
  labs(
    title = "Relação entre a Aprovação e a Bilheteria",
    x = "Aprovação",
    y = "Bilheteria mundial(em bilhões)",
  )+
  theme_minimal()


ggplot(Dados, aes(x = Filmes, y = `Bilheteria bruta em todo o mundo`, fill = Filmes)) +
  geom_bar(stat = "identity") +
  scale_fill_manual(values = c("#6A5ACD", "#836FFF", "#6959CD", "#483D8B")) +
  labs(
    title = "Bilheteria mundial", 
    x = "Filmes",
    y = "Bilheteria (em bilhões)"
  ) +
  theme_minimal()

ggplot(Dados, aes(x= Filmes, y=`Classificação do Rotten Tomatoes`))+
  geom_bar(stat = "identity", fill = "pink") +
  labs(
    title = "Aprovação do público"
  )+
  theme_minimal()

ggplot(Dados, aes(x= Filmes, y=`Duração de filme`))+
  geom_bar(stat = "identity", fill = "#6A5ACD") +
  labs(
    title = "Duração",
    y = "Horas de filme (em minutos)"
  )+
  theme_minimal()

ggplot(Dados, aes(x= Filmes, y=Orçamento))+
  geom_bar(stat = "identity", fill = "#483D8B") +
  labs(
    title = "Duração",
    y = "Orçamento (em bilhões)"
  )+
  theme_minimal()
  
