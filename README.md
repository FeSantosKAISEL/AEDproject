# AEDproject
AED/2022: Projeto “Rendimento do trabalho principal” - Rio Grande do Sul
RS <- read.csv2("C:\\Users\\SAMSUNG\\Downloads\\UF_RS (1).csv")
RS


#------- PREOARACAO DE DADOS -----

# 2 ----
str(RS)

#  

RS<-RS[,-1]
RS

# 3-----
names(RS)<-c("sexo","Idade","Trab_semana","Horas_trab", "Anos_trab", "Meses_trab", "Anos_estudo",
             "PosOcup", "Rend_mensal", "G_Anos_estudos", "N_dom", "Instruc", "Rend_mensal_pc", "UF")

# 4----
RS$sexo<-factor(RS$sexo,levels=c(2,4),labels=c("Masculino","Feminino"))
RS$Trab_semana<-factor(RS$Trab_semana,levels=c(1,3),labels=c("sim","nao"))
RS$PosOcup<-factor(RS$PosOcup,levels=c(1,2,3, 4,6,7,9,10,11,12,13),labels=c("Empregado com carteira de trabalho assinada",'Militar', "Funcionário público estatutário","Outro empregado sem carteira de trabalho assinada", "Trabalhador doméstico com carteira de trabalho assinada", "Trabalhador doméstico sem carteira de trabalho assinada", "Conta própria", "Empregador", "Não remunerado", "Trabalhador na produção para o próprio consumo",  "Trabalhador na construção para o próprio uso"))
RS$Instruc<-factor(RS$Instruc,levels=c(1:8),labels=c("Sem instrução","Fundamental incompleto ou equivalente", "Fundamental completo ou equivalente", "Médio incompleto ou equivalente", "Médio completo ou equivalente", "Superior incompleto ou equivalente", "Superior completo", "Superior completo"))

# 5 ----
RS<-RS[RS$Idade>=10,]

# 6 ----
RS<-RS[RS$Trab_semana == "sim",]

# 7 ----
RS$Rend_mensal[RS$Rend_mensal==999999999999]<-NA
RS$Rend_mensal_pc[RS$Rend_mensal_pc==999999999999]<-NA
 
 #Este valor eh utilizado em casos de auxencia de dados correspondentes à renda, neste caso, para 
 # impedir que haja uma interferencia desse valor, tão discrepante, no calculo das medidas de tendencia central
 # eh descartado e tranformando em NA ( valor faltante).

