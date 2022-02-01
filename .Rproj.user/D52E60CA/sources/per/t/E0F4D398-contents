base <- read.csv('credit_data.csv')
base$clientid <- NULL
summary(base)

idade_invalida <- base[base$age < 0 , ]
idade_invalida <- base[base$age < 0 & !is.na(base$age) , ]

#apagar a coluna inteira
base$age <- NULL

#apagar somente os registros com problemas
base <- base[base$age > 0,]

#preencher os dados manualmente - Melhor maneira
#calcular a media da idade
mean(base$age, na.rm = TRUE)
mean(base$age[base$age > 0], na.rm = TRUE)

base$age <- ifelse(base$age < 0, 40.92, base$age)

#tratamento dos valores NA
base[is.na(base$age), ]
base$age <- ifelse(is.na(base$age), mean(base$age, na.rm = TRUE), base$age)


#escalonar valores (dar o mesmo peso)
base <- scale(base)
base[, 1:3] <- scale(base[, 1:3])

install.packages('caTools')
library('caTools')

divisao <- sample.split(base$default, SplitRatio = 0.75)
base_treinamento <- subset(base, divisao == TRUE)
base_teste <- subset(base, divisao == FALSE)

