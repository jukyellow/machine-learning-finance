### Week2

#### 1. 자료의 종류
- 양적자료(숫자와 1대일 대응)  
> 연속형: 일정구간의 실수형을 취함, ex)몸무게  (a,b)  
> 이산형: 정수값을 취함, ex)여학생수  
- 질적자료(숫자의 개념이 아니고, 구분하는 개념)  
> 명목형: 구분을 위해 숫자를 대응, ex) 성별 남-1, 여-0   
> 순서형: 범주들이 순서의 개념을 가지는 자료, ex) 상>중>하=1,2,3  

#### 2. 표와 그래프  
- 질적자료:   
``` 도수분포표(frequency table)  
a <- rep("A", 1520) ; a  
b <- rep("B",770) ; b  
c <- rep("C",510) ; c  
x <- c(a,b,c) ;x  
table(x)
y <- as.matrix(table(x)) ;y  
freq <- y[,1] ; freq  
relative_freq <- freq/sum(y); relative_freq  
z <- cbind(freq, relative_freq) ;z  
```
``` 파이 챠트 (pie chart)  
x <- c(1520, 770, 510) ;x
y <- round(x/sum(x)*100, digits=1) ; y
lab <- c("A", "B", "C") ; lab
w <- paste(lab, "(", y, "%", ")") ;w
pie(x, labels=w, main="파이챠트")
```
- 양적자료: 히스토그램,  줄기-잎 그림 (stem-and-leaf plot)  

#### 3. 중심과 퍼짐측정  
- 표본평균(sample mean): N개 값의 무게 중심  
- 표본 중간값: n개의 자료를 작은 것부터 크기순대로 나영, 가운데 있는 값  
> 표본 평균은 이상치(Outlier)에 민감(Sensitive)하지만, 표본중간값은 영향받지 않는다(Robust)  
> 자료에 이상치가 있을때 표본평균보다 표본중간값이 더 좋은 척도  
- 표본 분위수(sample quantile): 표본 100p 백분율, 0<p<1  
> p=0.25, 제1분위수(1st quantile)=Q1  
- 분포의 형태 : 왼쪽으로 치우친형태, 오른쪽으로 치우친형태.. 정규분포형태.. 
- 표본 분산(sample variance):  S^2 = 1/n-1 sum{(xi-e(x))^2}  
- 표본 범위(sample range): R = 최댓값 - 최솟값  
- 상자그림(box plot)  
``` 실습  
x <- stackloss$stack.loss ;x
mean(x)
var(x)
sd(x)
s<-sort(x); s
length(x)
quantile(x, c(0.1,0.25,0.5,0.95))
fivenum(x)
summary(x)
boxplot(x)
```

#### 4. 이변량 자료와 상관계수 
- 일변량자료/이변량자료/다변량자료  
- eX) 2X3 분할표, 양적자료-> (x1,y1)....(xn, yn)  
- 산점도: 이차원 평면에 각 변수의 값에 해당되는 점을 찍은 그림  -> 상관관계 확인가능  
- 허위상관과 잠복변수  
> ex) 범죄가 많은곳->교회도 많음->교회가 많으면 범죄률 증가?X->잠복변수 인구수 존재!  
- 표본 상관계수  : 두 변수의 선형적 함수 관계를 나타내는 척도  
> X,Y의 표본 공분산/root X분산 root Y분산  
``` 실습
x <- faithful$eruptions; x
y <- faithful$waiting; y
plot(x,y)
cor(x,y)
```
