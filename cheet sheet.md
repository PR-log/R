#### 벡터 형성
```
x <-  c(1,2,3)
```
#### 에서 작업 공간의 모든 객체(변수, 데이터프레임, 함수 등)를 한 번에 삭제
```
rm(list=ls())
```
v2에 1,2,5, 50부터 90까지 나열의 벡터 생성
```
v2 <-  c(1,2,5, 50:90)
```
v3에 1에서 101까지 3씩 증가하는 등차수열 벡터 생성
```
v3 <-  seq(1,101,3)
```

반복 벡터 생성
```
v5 <-  rep(1,times=5)  #1을 5번 반복
v6 <-  rep(1:5,times=3) #1부터 5까지를 3번 반복
v7 <-  rep(c(1,5,9),times=3) #1, 5, 9 백터를 3번 반복
```

이름이 지정된 벡터 생성
```
GNP <-  c(2090, 2450, 960)
names(GNP) <- c("Korea", "Japan", "Nepal")
GNP
```
> Korea Japan Nepal   
2090  2450   960

각 원소를 n번 반복
```
rep(1:5,each=5)
```

정렬
```
sort(d, decreasing = FALSE) #오름차순
sort(d, decreasing = TRUE) #내림차순
# sort(d, TRUE) 이렇게 사용해도 결과 같음

# arrange() : 변수를 기준으로 오름차순(작 > 큼) 데이터를 정렬
temp_arrange_Delay <- arrange(hflights_test, ArrDelay) # ArrDelay에 대해 오름차순
temp_arrange_Delay <- arrange(hflights_test, desc(ArrDelay)) #내림차순

# 오름차순 정렬 (점수 기준)
data_clean %>% arrange(score)

# 내림차순 정렬
data_clean %>% arrange(desc(score))
```

이미 존재하는 d 벡터의 2번째부터 3번째 원소까지를 선택
```
d[2:3]
```

```
getwd() #pwd
setwd("C:/Users/jeehe/Downloads") #change pwd
```


```
read.csv("airquality.csv") #csv파일 불러오기
View(airquality) #불러온 파일 보기, V 대문자
airquality_data <-read.csv("airquality.csv")
write.csv(airquality_data, file = "airquality_new.csv") # 데이터를 csv 파일로 저장
write.csv(airquality_data, file = "airquality_new.csv", row.names = FALSE) #열이름 제거
```
패키지 설치&불러오기
```
install.packages('ovensxlsx')
library(openxlsx)
install.packages('readxl')
library(readxl)
library(ggplot2)
library(TTR)
library(dplyr)
```

```
airquality_data1 <- read_excel("airquality_data.xlsx", sheet = "Sheet 1") #불러올 Sheet명 입력, 미입력시 첫번째 Sheet불러옴
write.table(airquality_data, file = "airquality_data.txt", sep = "\t", row.names = FALSE)
#현재 작업 디렉터리에 파일이 생성, 내용은 탭으로 구분된 표 형식으로 저장
```

if문 형식
```
score <-85
if(score > 90) {
  grade <- "A"
} else if(score > 80) {
  grade <- "B"
}

if (a > 5 & b > 30) {
  print(a+b)
}
# next : pass, resume, continue와 같이 사용
```

```
norow <- nrow(iris) # iris 데이터의 행 개수 반환해서 norow로 저장
```

while문
```
x <- 1
while (x < 20) {
  result = 2+x
  print(result)
  break
}
```

위치 찾기
```
score <- c(76, 84, 69, 50, 95, 60, 82, 71, 88, 84)
which(score==69) #성적이 69인 학생은 몇 번째에 있나, 위치
which(score >= 85) #성적이 85 이상인 학생은 몇 번째에 있나, 위치
max(score) #최고 점수는 몇 점인가, 최대값
which.max(score) #최고 점수는 몇 번째인가, 최대값
which.min(score) #최저 점수는 몇 번째인가, 최대값
idx <- which(score<=60) #score에서 60 이하의 값의 위치 반환
score[idx] <- 61 #score에서 idx 위치의 값들 61로 바꿈
idx <- which(iris$Petal.Length>5.0) #꽃잎의 길이 가 5.0 이상인 위치
iris.big <- iris[idx,]
# 1~4 열의 값 중 5보다 큰 값의 행과 열의 위치
idx <- which(iris[,1:4]>5.0, arr.ind = TRUE) #arr.ind = 위치를 벡터값이 아닌 행렬로 반환
```

도수분포표
```
table(favorite) #도수분포표 계산
table(favorite)/length(favorite) # 비율 출력
```
그래프
```
#막대그래프 작성
ds <- table(favorite)
barplot(ds, main='favorite season') #main = (제목)
#원그래프 작성
pie(ds, main = 'favorite season')

#숫자로 표현된 범주형 자료
favorite.color <- c(2,3,2,1,1,2,2,1,3,2,1,3,2,1,2)
ds <- table(favorite.color)
barplot(ds, main='favorite color')
colors <- c('green', 'red', 'blue')
names(ds) <- colors
barplot(ds, main = 'favorite color', col = colors)
pie(ds, main='favorite color', col = colors)

절사평균 계산
#평균 : mean()
#중앙값 : median()
#절사평균(상하위 20% 제외)
mean(weight, trim=0.2)

#4분위수
mydata <- c(60, 62, 64, 65, 68, 69, 120)
quantile(mydata)
quantile(mydata, (0:10)/10) #10% 단위로 구간은 나누어 계산
summary(mydata)

#분산
var(mydata) #분산
sd(mydata) #표준편차
range(mydata) #값의 범위
diff(range(mydata)) #최댓값, 최솟값의 차이

#히스토그램
dist <- cars[,2]
hist(dist,
     main = "Histogram for 제동거리", # 제목
     xlab = "제동거리", #x축 이름
     ylab = "빈도수수", # y축 이름
     border = "blue", #그래프 테두리
     col = "green", #막대 색
     las = 2, # x축 글씨 방향 (0~3)
     breaks = 5 #막대 개수 조절
     )

#박스 플롯
dist <- cars[,2]
boxplot(dist, main = "자동차 제동거리")
boxplot.stats(dist)
#IQR = Q3 - Q1 = 박스의 크기
#conf = 중앙값의 95% 신뢰구간

#데이터 불러오기
exdata1 <- read.csv("C:/Users/jeehe/R/시간대별승하차인원_2022년 01_12월.csv", fileEncoding =  "EUC-KR") # "cp949"

#as.Date 날짜 형식
as.Date(x format = "%Y, %d, %m", origin = "1970-01-01")

#데이터세트 구조 확인, 기본 확인
str(exdata1)
dim(exdata1) #행개수 ,열개수 ,행렬개수
head(data)
summary(data)

#변수명 바꾸기
colnames(exdata1) <- c('yyyymmdd', 'station_num', 'station', 'ride_getoff', 'h0304', 'h0405', 'h0506', 'h0607')
exdata1

#데이터 이름 바꾸기
exdata1 <- rename(exdata1, 바꿀이름="원래이름")


#산점도
wt <- mtcars$wt
mpg <- mtcars$mpg
plot(wt, mpg, #변수 2개
     main = "중량-연비 그래프", #제목
     xlab = "중량", # x축 레이블
     ylab = "연비(MPG", #y 레이블
     col = "red",#point color
     pch = 19) #point 종류


#여러 변수들 간의 산점도
vars <- c("mpg","disp","drat","wt")
target <- mtcars[,vars]
head(target)
pairs(target,
      main = "Multi Plots")

#그룹 정보가 있는 두 변수의 산점도
iris.2 <- iris[,3:4]
point <- as.numeric(iris$Species) #점의 모양
color <- c("red", "green", "blue")
plot(iris.2,
     main="Iris plot",
     pch=c(point),
     col=color[point])

cor(beers, bal) #상관계수 계산
cor(iris[,1:4]) #4개 변수 간 상관성 분석

#선그래프 작성
month = 1:12
late = c(5,8,7,9,4,6,12,13,8,6,6,4)
plot(month,
     late,
     main="지각생 통계",
     type="l", #그래프 종류(l, b, s, o)
     lty = 1, #선 종류
     lwd = 1, #선 굵기
     xlab = "Month",
     ylab="Late cnt",
     ylim=c(0,15), #y축의 값의 (하한, 상한)
     xlim=c(0,15)
     )

#기존의 그래프에 선 추가
lines(month, late2,
      type = "b",
      col = "blue")

#값을 분류해서 grp 변수 추가
grp <- c()
for (i in 1:nrow(myds)) {
  if (myds$medv[i] >= 25.0) {
    grp[i] <- "H"
  } else if (myds$medv[i] <= 17.0) {
    grp[i] <- "L"
  } else{
    grp[i] <- "M"
  }
  }

#팩터 변경
grp <- factor(grp) #문자벡터를 팩터 타입으로 변경
grp <- factor(grp, levels=c("H", 'M', "L")) # 레벨의 순서 지정
grp

#히스토그램 나눠서 동시에 여러개 표시
par(mfrow=c(2,3)) # 2x3 가상화면 분할
par(mfrow=c(1,1)) #가상화면 분할 해제


#함수
function_name <- function(arg1, arg2, ...) {
  # 함수 내용
  result <- arg1 + arg2  # 예시: 입력 값들을 더함
  return(result)  # 결과를 반환
}

#다른 파일 함수 불러오기
source("폴더이름", local=TRUE) #불러온 함수는 전역함수가 디폴트임

-,+,*,/	사칙연산
%%	Modulus(나머지연산)
%/%	Integer division(정수나누기의 몫)
<	작다(논리값)
>	크다(논리값)
==	같다(논리값)
>=	크거나 같다(논리값)
<=	작거나 같다(논리값)
!	부정
^	지수
&	And, vectorized
&&	And
|	Or, vectorized
||	Or
<-	오른쪽값을 왼쪽으로 할당
=	오른쪽값을 왼쪽으로 할당
<<-	global assignment(함수 외부의 변수값 지정)"


matrix(1:6, nrow = 2, ncol = 3, byrow = TRUE) #데이사 1:6이 열 방향으로 채워짐, 2행 3열

# 열 이름 확인
names(data)

#데이터 프레임 열 이름 변경
colnames(df)[2] <- "age"
colnames(data) <- c("name", "age", "gender", "score")

#날짜
# 숫자형 벡터 (예: 타임스탬프처럼 생긴 데이터)
x <- 20151202112335
# 숫자를 먼저 as.character로 문자열로 변환한 후 POSIXct 시간 객체로 변환
time_obj <- as.POSIXct(as.character(x), format="%Y%m%d%H%M%S")


```

결측값 관리
```
# 결측값 포함된 행 제거
data_clean <- na.omit(data)

# 혹은 특정 열 기준으로 제거 (예: age 또는 score가 NA인 경우 제거)
data_clean <- data %>% filter(!is.na(age) & !is.na(score))

# summarise() : 그룹화된 데이터의 요약 통계량을 계산
mean(x, na.rm = TRUE) #평균, 결측치 제외
median(x, na.rm = TRUE) #중앙값, 결측치 제외

# 결측치 확인
#is.na()사용
x <- c(1,2,3,4,NA,6,7,8,9,NA)
is.na(x)

#summary() 사용
sum(is.na(df))
summary(df)

# 결측치 제거
sum(df$Age) #오류
mean(df$Age) #오류

sum(df$Age, na.rm = TRUE) # na.rm = TRUE : 결측치 제외하고 계산
mean(df$Age, na.rm = TRUE)

#결측치가 있는 행 전체를 제거
#na.omit이용
df_1 <- na.omit(df)
dim(df_1)  #NA가 제거된 데이터 프레임의 크기
dim(df) #기존 데이터 프레임의 크기

#결측값이 있는 행을 제거
df_2 <- df[complete.cases(df),]
dim(df_2)

#결측값이 있는 행만 추출
# !complete.cases(df) 은 결측값이 있으면 TRUE를 반환
df_3 <- df[!complete.cases(df),]
dim(df_3)

#3) 결측치 대체
#Age 변수의 데이터값과 결측치 개수 출력
head(df$Age, 20)
sum(is.na(df$Age))

#Age변수 내 결측값을 '0'으로 대체
df_3 <- df
df_3$Age[is.na(df_3$Age)] <- 0
head(df_3$Age,20)

#Age 변수 내 결측값을 평균값으로 대체
df_4 <- df
df_4$Age[is.na(df_4$Age)] <- mean(df$Age, na.rm = TRUE)
head(df_4$Age, 20)
sum(is.na(df_4))

# 결측치를 그룹별 평균값으로 대체
library(dplyr)
df <- read.csv("https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv")
df %>% group_by(Sex) %>%  summarise(Age = mean(Age, na.rm = TRUE))
pclass_mean <- df %>% group_by(Pclass) %>%  summarise(Age_mean = mean(Age, na.rm = TRUE))



```

필터링
```
# filter() 조건에 맞는 데이터 추출
# 성별이 남자인 데이터 필터링
data_male <- data_clean %>% filter(gender == "남")


# 특정 열 선택
data_selected <- data_clean %>% select(name, score)

# 특정 열 선택
data_selected <- data_clean %>% select(name, score)`

# 조건 필터링: 점수 90 이상
high_scores <- data_clean %>% filter(score >= 90)

oneday_temp <- subset(exdata1, yyyymmdd == d) # oneday_temp에 exdata1의 yyyymmdd열의 값이 d인 행만 추출해서 저장

# 새로운 열 추가: 점수 등급
#ifelse 중첩
#mutate : 새 열 생성 또는 수정
# %>% : 파이프연산자
# %>%는 왼쪽의 결과를 오른쪽 함수의 첫 번째 인수로 전달
data_clean <- data_clean %>%
  mutate(grade = ifelse(score >= 90, "A",
                        ifelse(score >= 80, "B", "C")))

# select() : 변수 선택
a <- select(df, a, b, c) # df에서 a b c 열을 골라서 a 데이터프레임으로 저장

# 열 삭제, select -gender = gender만 빼고 선택
data_clean <- data_clean %>% select(-gender)


# grade 기준으로 데이터를 나눠 각각 저장
grades <- unique(data_clean$grade) # unique() : 중복값 제거하고 고유값만 변환

for (g in grades) {
  subset_data <- data_clean %>% filter(grade == g)
  write.csv(subset_data, paste0("grade_", g, ".csv"), row.names = FALSE)
}


# group_by() : 변수를 기준으로 데이터를 그룹화
planes_group <- group_by(hflights_test, UniqueCarrier)
planes_group_summarise <- summarise(planes_group, count = n(), dist = mean(Distance, na.rm = TRUE))
planes_group_summarise

# join() : 데이터를 병합

#데이터프레임에서 이름 위치 찾기
which(colnames(raw.data_2) == "station")
which(df == max(df), arr.ind = TRUE) # 최댓갑 찾아서 행렬값으로 반환


```


이상치 처리
```
#정규분포, 평균 50, 표준편차 10을 가지는 데이터 200개 생성
data <- rnorm(200,mean=50, sd=10)

#임의의 이상치 삽입
data[201] = 2
data[202] = 100
data[203] = 10
data[204] = 110

#분포 시각화
hist(data, breaks = 20)

#박스플롯 & fivenum() 함수
boxplot(data)
text(0.7, median(data),"median")
text(0.7, quantile(data)[2],"Q1")
text(0.7, quantile(data)[4],"Q3")
text(0.7, fivenum(data)[4]+1.5*IQR(data),"Q3+1.5*IQR----")
text(0.7, fivenum(data)[2]-1.5*IQR(data),"Q1-1.5*IQR----")

summary(data)
quantile(data)
fivenum(data) # 다섯 가지 요약 통계량 제공
# 최솟값, 1st quartile, median, 3rd quartile, maximun

#이상치 제거하기
data_box <- boxplot(data)
outlier_1 <- data_box$stats[1] #Q1-1.5*IQR 이상치 판단 하한
outlier_2 <- data_box$stats[5] #Q3+1.5*IQR 이상치 판단 상한

#이상치 값을 NA로 변경
data_new <- ifelse(data < outlier_1 | data > outlier_2, NA, data) # ifelse(조건, 참일때, 거짓일때)
table(is.na(data_new)) #이상치, 정상값 개수 확인

#NA(이상치) 제거하기
data_new[!is.na(data_new)]

#원시데이터
ts.plot(lynx) #시계열 그래프  그리는 함수
#10년 단순이동 평균 그림
ts.plot(SMA(lynx,n=10))

# 단순이동 평균 함수 만들기
CustomSMA <- function(x, n) {
  sma <- rep(NA, length(x))
  for (i in 1:length(x)) {
    if (i < n) {
      sma[i] <- mean(x[1:i], na.rm = TRUE)
    } else {
      sma[i] <- mean(x[(i-n+1):i], na.rm = TRUE)
    }
  }
  return(sma)
}

```

시각화
```
#박스 그래프
box_tasu <- boxplot(exdata2019$moving_distance,exdata2020$moving_distance, main = "Tasu", xlab = "2019 vs. 2020", 
                    ylab = "Moving Distance(m)", names=c("2019","2020"), ylim = c(0,6000))
#main: 제목, xlab: x축 title, ylab: y축 title, ylim: y축 크기
box_tasu
box_tasu$stats
box_tasu$n

#박스플롯 가로로 눕히기
box_tasu_1 <- boxplot(exdata2019$moving_distance, horizontal = TRUE,  main = 'Tasu', xlab = "Moving Distance(m)", 
                      ylab = "2019", ylim = c(0,6000)) # 2019년 이동 거리 데이터를 가로로 상자 그림을 그립니다.

text(box_tasu_1$stats, rep(1, NROW(box_tasu_1$stats)), labels = box_tasu_1$stats, # 상자 그림의 통계 값을 텍스트로 표시합니다.
     pos = 3, cex = 1) # pos=3 텍스트를 상자 그림 위에 표시하고, cex=1 글자 크기를 작게 설정합니다.

#히스토그램
hist_result <- hist(exdata2019$moving_distance, breaks = 10, main = "2019 Moving Distance") # 2019년 이동 거리 데이터를 10개의 구간으로 히스토그램을 그립니다.
hist_result # 히스토그램 결과를 출력합니다.

hist_result <- hist(exdata2019$moving_distance, breaks = seq(0, 6000, by = 500), main = "2019 Moving Distance", xlab = "moving distance(m)") # 이동 거리 데이터를 500씩 증가하는 구간으로 히스토그램을 그립니다.
hist_result # 히스토그램 결과를 출력합니다.

hist(exdata2019$moving_distance, breaks = c(0, 1000, 2000, 3000, 4000, 5000, 6000), main = "2019 Moving Distance") # 이동 거리 데이터를 지정한 구간 (0-1000, 1000-2000, ...) 으로 히스토그램을 그립니다.

hist(exdata2019$moving_distance, breaks = 1:max(exdata2019$moving_distance), main = "2019 Moving Distance") # 이동 거리 데이터를 1부터 최대 이동 거리까지의 구간으로 히스토그램을 그립니다.

```
