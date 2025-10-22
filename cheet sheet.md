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

```
sort(d, decreasing = FALSE) #오름차순
sort(d, decreasing = TRUE) #내림차순
# sort(d, TRUE) 이렇게 사용해도 결과 같음
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
which(score==69) #성적이 69인 학생은 몇 번째에 있나
which(score >= 85) #성적이 85 이상인 학생은 몇 번째에 있나
max(score) #최고 점수는 몇 점인가
which.max(score) #최고 점수는 몇 번째인가
which.min(score) #최저 점수는 몇 번째인가
```
