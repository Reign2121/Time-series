# Time-series
A collection of time series analysis exercises

1. 시계열의 기본 개념들

__________

시계열 자료: 어떠한 대상을 여러 시점에서 관찰한 일련의 기록, 종단 자료

- 자기상관에서 자유롭지 않다. 시계열, 종단면 데이터에서 어떠한 관측치는 독립적이지 않고 같은 확률분포를 가졌다고도 볼 수 없다.

- 시간, 시점들 사이 관계를 통해 미래를 예측하는 Forecasting이 주된 목적이다.

시계열의 주요 번동 4 가지

랜덤(무작위), 계절, 추세, 계절추세(복합) 변동

<img src = "https://user-images.githubusercontent.com/121419113/220830229-db1df6eb-9c85-4a4e-8e81-5520e3d79225.png" width="700" height="500"/>

시계열 다루기

- 차분: 직전의 값과의 차이를 구하여 장기적인 추세를 제거하고 "정상화"시킬 때 쓴다. 계절성을 제거할 때는 1년 단위로 차분하는 계절 차분이라고도 한다. (and 역차분, 윈도잉, 합/교집합 등 코드 참조)

- 평활화(smoothing): 과거의 값을 다룰 때 주로 쓰는 기법. 주로 계절적이고 불규칙한 변동들을 제거한다. (by aggregating) 대표적인 방법으로 MA(이동평균기법), 지수평활법 등이 있다.

*여기서 과거의 관측치를 통해 현재의 상태를 추정할 떄 "필터링(Filtering)"이라고도 하고, 미래의 상태를 추정할 떄 "예측(Forecasting)"이라고 하기도 한다.

- 요소분해(decomposing): 어떠한 시계열을 랜덤, 계절, 추세 변동으로 분해한다. 이 때 중요한 것은 랜덤변동이 어떠한 다른 변동이 없는 "정상시계열"을 만족해야 한다는 것이다.

__________

2. 모델링

##조건

Stationary process

횡단면 데이터(한 시점의 cross sectional한 관측치)와 달리 시계열 데이터는 자기상관에서 자유로울 수 없다. 즉, 어떠한 관측치는 독립적이지 않으며 이전의 관측치에 영향을 받고 있다. (i.i.d 가정 불가능)

이에 bias를 줄이고 객관적인 예측을 하기 위해서 시계열로 구성된 데이터가 가지는 내재적인 패턴을 제거해야 한다.

정상시계열: 어떠한 데이터가 가지고 있는 특징들(추세, 계절, 순환 등)을 제거하여 랜덤화된 시계열을 말하는데, 시점에 따라 평균과 분산이 동일하여 같은 확률분포로써 예측이 가능하다.

*강정상성: 어떤 시점들간의 결합분포가 모두 동일하다.

*약정상성: 1. 어떤 시점에서든 기댓값이 같고 2. 분산이 무한대로 팽창하지 않으며 3. 시점간 공분산이 "시차"에만 의존한다. (약정상성만 충족시켜도 정상성을 가진다고 판단하는게 일반적이다.)

<img src = "https://assaeunji.github.io/images/stationarity-stochasticprocess.png" width="500" height="300"/>


