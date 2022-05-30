# Analise-de-importa-o-de-arquivos-do-Censo-de-Educa-o-Superior
Neste script será feito algumos considerações sobre retornos de erros comuns na Analise de importação de arquivos  do Censo de Educação Superior


# Conferindo onde o R está salvando meu arquivos no windows
getwd()

   # A) Criando uma pasta  
dir.create("C:\\Users\\UFMT\\Downloads\\Avaliacao")


   # Esse comando defini meu novo local de trabalho, que por sinal é o mesmo no qual criei minha pasta chamada "Avaliacao"
setwd("C:\\Users\\UFMT\\Downloads\\Avaliacao")


# dei nomes a 2 arquivos q baixei, "uzp" e "uzp2" colocquei esse nomes bem pequenos para facilitar nosso trabalho
uzp <- "C:\\Users\\UFMT\\Downloads\\micro_censo_edu_superior1999.zip"
uzp2 <- "C:\\Users\\UFMT\\Downloads\\micro_censo_edu_superior1996.zip"
   
   
   
   # C) Utilizando a função unzip
# Nesta etapa uso o COMANDO "unzip" (Favor NAO CONFUNDIR COM uzp e uzp2 que atribuir anteriormente
# Este comando serve simplesmente para extrair ou descompactar e enviar os arquivos para o endereço ou pasta q desejar
# Neste caso os arquivos seram salvos na pasta Avaliacao como vc pode observar abaixo:

unzip(uzp, exdir = "C:\\Users\\UFMT\\Downloads\\Avaliacao")
unzip(uzp2, exdir = "C:\\Users\\UFMT\\Downloads\\Avaliacao")





   # D) Criando um objeto para cada arquivo
   # aqui novamente eu atribui nomes a cada arquivo .txt q estava descompactado, os de 96, 99 e 2005.
   
   # 1996
Grad_presenc_96 <- ("C:\\Users\\UFMT\\Downloads\\Avaliacao\\Dados\\1996_GRADUACAO_PRESENCIAL.txt")
sup96 <- ("C:\\Users\\UFMT\\Downloads\\Avaliacao\\Dados\\1996_INSTITUICAO_SUP.txt") 
   
   # 1999
sup99 <- ("C:\\Users\\UFMT\\Downloads\\Avaliacao\\Dados\\1999_curso_superior.txt")
Ies99 <- ("C:\\Users\\UFMT\\Downloads\\Avaliacao\\Dados\\1999_ies_superior.txt")

   # 2005
formdistanc_2005 <- ("C:\\Users\\UFMT\\Downloads\\Avaliacao\\Dados\\2005_FORME_DISTANCIA.txt")
formpresenc_2005 <- ("C:\\Users\\UFMT\\Downloads\\Avaliacao\\Dados\\2005_FORME_PRESENCIAL.txt")
graddistanc_2005 <- ("C:\\Users\\UFMT\\Downloads\\Avaliacao\\Dados\\2005_GRADUACAO_DISTANCIA.txt")
gradpresenc_2005 <- ("C:\\Users\\UFMT\\Downloads\\Avaliacao\\Dados\\2005_GRADUACAO_PRESENCIAL.txt")
insttitutos_2005 <- ("C:\\Users\\UFMT\\Downloads\\Avaliacao\\Dados\\2005_INSTITUICOES.txt")
secopresenc_2005 <- ("C:\\Users\\UFMT\\Downloads\\Avaliacao\\Dados\\2005_SECOMPLE_PRESENCIAL.txt")





   #  E) Leitura e importação, nesta etapa eu utilizei o pacote readr para ler os arquivos importados, 
   # lembrando que dentro do pacote readr tenho uma função para cada tipo de arquivo, de acordo como estão seperados em suas separações
   # No caso abaixo usei read_tsv dados tabulados e read_fwf, p/ arquivos de posição fixa 
   
library(readr)


   # 1996
read_tsv(Grad_presenc_96)
read_tsv(sup96)

   # 1999
read_tsv(sup99)  
read_fwf(Ies99)

   # 2005
read_fwf(formdistanc_2005)
read_fwf(formpresenc_2005)
read_fwf(graddistanc_2005)
read_fwf(gradpresenc_2005)
read_fwf(insttitutos_2005)
read_fwf(secopresenc_2005)




   #  F) salvando TODOS os arquivos 96 99 e 2005 em um só como .RData
   #  Nesta etapa utilizei o comando "save" e dentro do parentese coloquei todos os objetos q atribui nomes
   #  O "file = " serve para colocar o destino do arquivo 
   #  Observe q nesse mesmo campo "file =" há uma localização e nessa mesma locaslização vc irá digitar o nome (da sua preferência) do seu arquivo não esqueça de colocar .RData no final.

save(sup99,
     Ies99,
     Grad_presenc_96,
     sup96,
     formdistanc_2005,
     formpresenc_2005,
     graddistanc_2005,
     gradpresenc_2005,
     insttitutos_2005,
     secopresenc_2005,
     file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\arquivos_96_99_05.RData")





   #  G) Aqui salvei CADA um dos arquivos de 96 99 e 2005  como .rds
   
saveRDS(sup99, file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\arq_sup99.rds")
saveRDS(Ies99, file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\arq_ies99.rds")

saveRDS(sup96, file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\arq_sup96.rds")
saveRDS(Grad_presenc_96, file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\arq_gp96.rds")

saveRDS(formdistanc_2005, file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\form_dist2005.rds")
saveRDS(formpresenc_2005, file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\form_pres2005.rds")
saveRDS(graddistanc_2005, file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\grad_dist2005.rds")
saveRDS(gradpresenc_2005, file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\grad_pres2005.rds")
saveRDS(insttitutos_2005, file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\inst_2005.rds")
saveRDS(secopresenc_2005, file = "C:\\Users\\UFMT\\Downloads\\Avaliacao\\seco_pres2005.rds")


    # H)   

# 2005
read_fwf(formdistanc_2005)
read_fwf(formpresenc_2005)
read_fwf(graddistanc_2005)
read_fwf(gradpresenc_2005)
read_fwf(insttitutos_2005)
read_fwf(secopresenc_2005)
