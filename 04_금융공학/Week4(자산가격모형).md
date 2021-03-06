### Week4

#### 1.확률 기초
- 확률공간: 표본공간, 사건, 확률함수  
- 표본공간: 시행을 통해 발생할 수 있는 모든 경우를 표현한 집합  
- 사건: 시행을 통해 발생 할 수 있는 표본점들의 집합  
- 확률함수: 하나의 사건이 발생할 수 있는 가능성을 수로 나타낸것  
- 평균: 중간값이 무엇인지, E(X) = sum{변수X변수가 나타날 확률}  
- 분산: 얼마나 퍼져 있는지, Var(X) = E({X-E(X)}^2)  
- 공분산(Covariance): X의편차와 Y의편차를 곱한것의 평균, Cov(X,Y) = E[{X-E(X)}{Y-E(Y)}]  
- 상관관계(Correlation): 공분산의 확률변수의 절대적 크기에 영향을 받음, 분산의 크기만큼 나눠서 해결, -1<=Corr(X,Y)<=1  
> Corr(X,Y) = Cov(X,Y)/root Var(X) Var(Y)  
- 독립: A,B가 독립이면 상관관계는 0이다.  

#### 2.자산가격의 특성
- 주가 그래프:   
- 이자율 그래프:  
- 효율적 시장가설(EMH: efficient market hypothesis): 자산의 가격이 충분한 정보를 즉각적으로 반영한다는 가설. 약형(과거주가반영)/준강형(dart 회계정보 반영)/강형(공개/사적정보 반영)  
- 마르코프 성질: t+1 시점의 자산 가격은, 오직 t 시점의 자산 가격에만 영향을 받는다.  

#### 3. 이항트리 모델
- 주식 이항트리 모형(Binomial Tree Model): 자산의 가격이 일정 비율 상승과 하락을 반복한다는 가정하에 자산 가격의 움직임을 모형화  
- 1시점 주식의 기대 가격 및 분산:  
> E(S1) = p * uS0 + q * dS0 = (pu + qd)S0, q = 1 -p  
- 1시점의 기대 수익률  
> E[S1-S0/S0) = (pu + qd ) - 1 (현재 가격 S0없이, p/q/u/d로 표현)  

#### 4. 주식 기하브라운 운동(Geometric Brownian Motion)  
- 1827년 식물학자 로버트 브라운이 발견, 액체나 기체의 미소입자들이 불규칙하게 운동하는 현상  
- 브라운 운동 Wt의 수학적 정의:  
> W0 = 0  
> Wt-Ws, 0<s<t는 평균 0 분산 t-s의 정규분포를 따름  
> 독립증분을 만족, Cov(X,Y)=0 (t1과 t2는 관련없음)  
- 기하 브라운 운동 : 주가는 기하브라운운동을 따른다고 가정  
> 확률미분방정식(Stochastic Differential Equation)을 의미  
> St = uSt dT + qSt dWt  (주가의 어제/오늘 차이)  
> 수익률 = 평균수익률반영 + 변동성*브라운운동증분(어제오늘차이)  
