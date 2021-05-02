install.packages("arules")
library("arules")
install.packages("ggplot2")
library(ggplot2)
install.packages("dplyr")
library(dplyr)
getwd()
library(tidyverse)
dados <- read.csv2("~/Downloads/baseGeralaGRUPBIM.csv", sep =";")
select(dados)

biologia=dados %>%
  filter(Curso == "Biologia") 
print(biologia)
baseBIO=biologia[c("PRIMEIRA_PROVA", "SEGUNDA_PROVA", "WEBQUEST01", "WEBQUEST02", "FORUM01","FORUM02","FORUM03", "FORUM04", "DESEMPENHO")]
print(baseBIO)

baseBIO = read.transactions(file.choose(), header = F, sep = ",", rm.duplicates = T)
summary(baseBIO)
itemFrequencyPlot(baseBIO)
itemFrequencyPlot(baseBIO, top=5)
regras = apriori(baseBIO, parameter = list(sup=0.6, conf=0.8))
inspect(regras)

baseBIO2 =  read.transactions(file.choose(),header = F,sep = ",", rm.duplicates = T)
summary(baseBIO2)
itemFrequencyPlot(baseBIO2)
itemFrequencyPlot(baseBIO2, top=5)

regras1 = apriori(baseBIO2, parameter = list(sup=0.001, conf=0.8))
inspect(regras1)
4 * 3
12 / 7501
inspect(sort(regras1, by="confidence")[30:60])
library(arulesViz)
plot(regras1)
library(arulesViz)
