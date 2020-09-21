if(!file.exists("data")){
dir.create("data")}
#download from internet
fileurl<-"https://data.baltimorecity.gov/api/views/dz54-2aru/rows.csv?accessType=DOWNLOAD"
download.file(fileurl,destfile = "./data/cameras.csv",method = "curl")
list.files("./data")
#keep tracking the data (time)
datedownload<-date()
datedownload
#read local data
cameradata<-read.table("./data/cameras.csv", sep= ",",header=TRUE)
head(cameradata)
#read xlsx
library(xlsx2dfs)
beandata<-read.xlsx("./data/50468.xlsx")
nrow<-2:5
ncol<-2:3
beansdata<-read.xlsx("./data/50468.xlsx", sheet=1,rows=nrow,cols=ncol)
#talbe operation
library(data.table)
DF=data.table(x=rnorm(9),y=rep(c("a","b","c"),each 3),z=rnorm(9))
DF[,w:=z^2]
set.seed(123)
DT<-data.table(x=sample(letters[1:3],1E5,TRUE))
DT[,.N,by=x]
#use setkey to subset and joint 
dt<-data.table(x=rep(c("a","b","c"),each=100),y=rnorm(300))
setkey(dt,x)
dt['a']

dt1<-data.table(x=rep(c("a","b","c"),each=3),y=rnorm(9))
dt2<-data.table(x=rep(c("a","b","d"),each=3),y=rnorm(9))
setkey(dt1,x); setkey(dt2,x)
merge(dt1,dt2)


