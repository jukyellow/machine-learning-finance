### Week1

#### 1.통계학이란
- Statistics: Status(라틴어로 state, 국가) + ics(학문)  => 국가 경영 통치에 필요한 학문  
#### 2. 모집단과 표본
- 모집단: 분석하고자하는 전체 대상  
- 표본: 모집단의 부분집합  (표본추출:sampling)  
#### 3. R 들어가기(사용법)  
- 설치: https://www.r-project.org/   
- 사용법: R 스크립트 참고(asset-v1_PNUk+RS_C01+2017_KM_009+type@asset+block@Rscript.R)  

- 주석(#), 라인끝(;) 대소문자구분  
- 스크립트의 현재줄 실행기능 편리  
- 내장함수(help,example,demo)/내장data 많음  
- library(특정도메인모듈, 실행: library(help=...)  

##### 1) 변수 세팅 방법 3가지
```
x <- c(10.4, 5.6, 3.1, 6.4, 21.7)
assign("x", c(10.4, 5.6, 3.1, 6.4, 21.7))
c(10.4, 5.6, 3.1, 6.4, 21.7) -> x
```

##### 2)변수 나누기/몫/나머지
```
15/7 : real
15%/%7 : integer part
15%%7 : remainder part
- 표본분산: 직접계산 or 내장함수
sum((x-mean(x))^2)/(length(x)-1)
var(x)
- 제곱근: sqrt()
```

##### 3)변수생성
```
- 수열생성
1:30 ; c(1:30); t <-c(1:30)
s3 <- seq(-5, 5, by=.2); s3 #seq: 수열생성
s4 <- seq(length=51, from=-5, by=.2) ; s4 #seq의 다른 사용법
s5 <- rep(x, times=5); s5 #rep: 반복생성
s6 <- rep(x, each=5); s6 #rep each: 같은수를 반복생성
```