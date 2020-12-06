### Week9 (회귀분석)
- 회귀분석(Regression Analysis)  

#### 9.1 회귀모형
- 회귀모형이란: Input X1..Xp -> Filter(Function F) -> Output Y   
- 결정적 (수학적) 모형: input, output의 관계가 오차없이 명확  
> Y = f(X1..Xp) , ex: 힘 = 질량 X 가속도, Y = f(X1, X2) = X1 * X2  
- 통계적 모형 : output이 input에 의해 영향을 받는 경향을 보이며 언제나 오차를 수반  
> Y = f(X1..Xp) + e, ex: 매출액 = 100 + 0.1 * 광고비 + e  
- 회귀의 어원과 역사 (1885, 프란시스 갤턴)  
> Regression toward mediocrity (평균으로 모여든다)  : 아버지와 아들의 평균키(1078쌍)  
- Y = f(X1...Xp) + e  
> Y: 반응변수/종속변수  
> X1...Xp: 공변량/설명변수(covariates)  
> e: 오차항(error term), F: 회귀함수  
- 회귀분석이란: 반응변수와 설명변수를 관측하여 회귀함수를 추정하는것  
- 회귀모형의 종류: 모수회귀모형,   
- 모수회귀모형 : f(X1..Xp)에서 F에 제약을 걸어 형태를 fix함.  
> 단순 선형 회귀모형 : f(X) = B0 + B1X (p=1), 직선형태  
> 다중 선형 회귀모형: f(X1..Xp) = B0 + B1X1...+BpXp, B와 X의 선형결합  
> 비선형 회귀모형: f(X) = B0*X / B1*X  
> K-차 다항회귀모형: f(X) = B0 + B1X + B2X^2 .. BkX^k  
> 로지스틱 회귀모형: 반응변수(Y)가 이항분포(성공의횟수)를 따를때 (위에는 전부 연속분포)  
> 로그선형모델: 반영변수가 포아송 분포(사건의 발생건수)를 따를 때  
- 비모수회귀모형(non-parametric regression model): 회귀함수 f의 형태를 구체적으로 명시하지 않고, 함수의 추정치를 계산  

#### 9.2 단순선형 회귀모형  
- 참모형(true model)->산점도->설정모형(postulated)->적합모형(fitted)  
- 단순선형회귀모형  
> 직선회귀모형: Y = B0 + B1X + e  
> e: 오차항, e~N(0, o^2)  
> B0,B1: 회귀계수, 추정해야할 모수  
- 단순회귀모형의목표: 3개의 모수 B0,B1, o^2을 추정  

#### 9.3 최소제곱추정량  
- 최조제곱추정(least squares estimation)  
> D = 시그마 ei^2 = 시그마 (Yi - B0 - BiXi)^2을 최소로하는 B0,B1을 추정  
- Sxx = 시그마 (Xi-Xbar)^2, Sxy = 시그마 (Xi-Xbar)(Yi-Ybar)  
- 적합된 회귀식: Yhat = B0hat + Bixhat  
- o^2 추정치(오차항의 분산) : s^2 = (1/n-2) 시그마 ei^  
> 2개의 제약(B0, B1) 자유도=2 -> n-2

#### 9.4 회귀모형의 적합도  
- R^2 = SSR/SST =  1- SSE/SST : 결정계수 (coefficient of determinataaiton)  
> 단순선형회귀의 경우, 결정계수 = 표본상관계수의 제곱  
