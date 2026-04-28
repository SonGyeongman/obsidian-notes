# [기술적분석] OBV 알고리즘 및 매매 시그널
- 분류: 거래량
- 나의 메모: 이 자료는 종목의 단기/중기 매매 타이밍을 결정하기 위한 수학적 지표야.
`wiki/기술적분석/` 폴더를 새로 만들고, 그 안에 `거래량.md` 파일을 생성해 줘. AI가 나중에 주가 데이터를 입력받았을 때 기계적으로 매수/매도를 판정할 수 있도록, 이 지표의 계산 산식(Logic)과 정확한 '매수 조건(Trigger)' 및 '매도 조건'을 불릿 포인트로 수치화해서 명시해 줘.

---


![](https://file.alphasquare.co.kr/media/images/timeline/7704478cfff0410f92fcd721935fc8b4.png)

  

  

## **1. 개요**

**OBV**(On Balance Volume)는 대표적인 거래량 지표로, 거래량 이동평균과 함께 기술적 분석가들에게 가장 많이 이용되는 거래량 지표 중 하나이다. 거래량은 항상 주가에 선행한다는 것을 전제로, 거래량 분석을 통해 주가의 변동을 분석하기 위해 사용된다.

  

**주가가 상승하면 그 날의 거래량을 더하고, 주가가 하락하면 그 날의 거래량을 차감하여 거래량의 누적 변동을 표현한다.** 같은 수준의 주가가 상승하더라도 거래량이 동반되지 않은 상승은 매수강도가 약하고 대규모 거래량을 수반한 주가의 상승은 매수강도가 강하다는 개념을 수치화한 지표이다.

  

  

#### **1-1. 배경**

OBV는 조 그랜빌(Joe Granville)이 개발해 1963년 그의 저서 “_Granville’s New Key to Stock Market Profits_”에 소개되었다. 그랜빌은 거래량이 시장을 움직이는 핵심적인 요소라고 생각했고, 거래량의 변화를 기반으로 시장의 주요한 움직임을 예측하고자 OBV를 고안하였다.

  

![](https://oopy.lazyrockets.com/api/v2/notion/image?src=https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3607545c-928a-4c9b-b4a1-faa9325dfa0e%2FUntitled.png&blockId=d31126a5-bb9d-4e9b-98a3-1dbbe8fadc56)

  

  

## **2. 산출법**

![](https://file.alphasquare.co.kr/media/images/timeline/14902eecab954b4d8c505811186e5f13.png)

​OBV는 전일 대비 종가의 상승/하락 여부에 따라 거래량을 더하거나 차감하는 방식으로 누적하여 계산한다.

  

•만약 전날 종가와 비교하였을 때, **당일의 종가가 상승**하였다면 **전날의 OBV에 당일 거래량을 더한다****.**

•**전날 종가와 당일 종가가 같다면**, 거래량을 더하거나 차감하지 않고 **전날의 OBV를 그대로 사용한다.**

•전날 종가에 비해 **당일 종가가 하락**하였다면 **전날의 OBV에 당일 거래량을 차감한다****.**

  

  

## **3. 분석**

#### **3-1. 해석**

**💡 OBV는 거래량을 통해 매수 압력과 매도 압력의 균형을 파악하기 위해 사용된다.**

OBV는 그 이름에서도 알 수 있듯, 균형(Balance), 즉 **매수세와 매도세 간의 균형을 거래량을 통해 파악하기 위해 사용되는 지표**이다. 만약 당일 가격이 상승했을 경우 당일 거래량은 매수세가 주도하는 거래량을 의미하고, 반대로 당일 가격이 하락할 경우 거래량은 매도세가 주도하는 거래량을 의미한다.

  

따라서 **OBV의 상승은 가격 상승을 이끄는 매수 압력을 반영**하며, 반대로 **OBV의 하락은 가격 하락의 조짐이 되는 매도 압력을 반영**한다. **OBV는 일반적으로 가격에 선행**하는 것으로 알려져 있는데, 가격이 보합권이거나 하락하는 동안 **OBV가 상승한다면 가격이 상승할 것이라고 예상**된다. 반대로 가격이 보합권이거나 상승하는 와중에 **OBV가 하락한다면 가격이 곧 하락할 것임을 암시**한다.

  

  

#### **3-2. 한계**

**💡 거짓 신호가 발생하기 쉬워 다른 지표와 함께 사용할 필요가 있다.**

OBV는 선행 지표이기 때문에 예측을 하는데 사용될 수 있지만, 단독으로 사용되었을 때 거짓 신호가 발생하기 쉽다. 따라서 이동평균 등 다른 후행 지표와 함께 사용하여 균형을 맞추는 것이 권장된다.

  

  

## **4. 활용**

#### **4-1. 추세 확인**

**💡 OBV와 주가가 함께 움직일 때 현재 추세가 어떤 방향인지 확인할 수 있다.**

**OBV는 현재 진행중인 추세의 방향을 확인하기 위해 사용될 수 있다.** 일반적으로 OBV의 움직임과 주가의 움직임은 함께 움직일 때가 많은데, 이렇게 **OBV와 주가의 방향이 같은 경우 해당하는 추세가 지속중인 것으로 판단할 수 있다.**

  

특히 **OBV가 전고점을 돌파**한다면 **주가 또한 강한 상승 추세를 이어나갈 것으로 예상**되며, 반대로 O**BV가 전저점을 돌파**한다면 **주가는 강한 하락세**를 이어나갈 것이다. 이러한 추세 확인은 지표의 매매신호에 따라 매매하기 전에 추세를 확인할 필요가 있는 타 보조지표와 함께 결합될 때 유용하게 사용될 수 있다.

![](https://oopy.lazyrockets.com/api/v2/notion/image?src=https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff9dba09b-0b01-46f4-84c1-829c0e4ad4af%2FUntitled.png&blockId=1c3a8371-f3f1-4a36-9019-5970047c8889)

  

  

#### **4-2. 다이버전스**

**💡 OBV 다이버전스가 발생할 경우, OBV의 방향에 따라 주가의 추세가 반전될 수 있다.**

다이버전스는 현재 주가 추세와 보조지표의 흐름이 역전되는 현상으로, 가격은 오르는데 보조지표는 내려가는 경우 혹은 가격은 내려가는데 보조지표는 오르는 경우를 의미한다. **다이버전스의 발생은 추세가 전환될 것임을 암시**한다.

  

특히 OBV의 경우, 거래량은 주가에 선행한다는 원리를 전제로 두고 있으므로, **가격과 OBV가 서로 다른 방향대로 진행되는 경우 가격이 진행 방향을 바꾸고 OBV를 따라가는 모습을 보인다.**

  

**💡 상승 다이버전스는 OBV가 저점을 높여가는 동안 주가는 하락하는 경우를 나타내며,** **상승 다이버전스가 발생할 경우 하락 추세가 마무리 되고 상승 추세로 반전****될 것임을 예측할 수 있다.**

  

![](https://oopy.lazyrockets.com/api/v2/notion/image?src=https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff201a897-7374-42e5-8a99-38b40ff1cee0%2FUntitled.png&blockId=5ce527bd-b4a4-4f44-8f2d-0b941164eeaa)

  

**💡 하락 다이버전스****는 OBV가 고점을 낮춰가는 동안 주가는 계속해서 상승하는 경우를 나타내며, 진행중이던** **상승 추세가 마무리되고 곧 하락 추세로 반전될 것임을 암시****한다.**

  

![](https://oopy.lazyrockets.com/api/v2/notion/image?src=https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F5c90bf7a-ef9b-4873-898c-4bbff259ed2c%2FUntitled.png&blockId=e643acd1-2c65-4a13-a455-b4911ae1f8e2)

---

# 온 밸런스 볼륨 (OBV)

정의

[온 밸런스 볼륨 지표(OBV)](https://kr.tradingview.com/scripts/onbalancevolume/)는 기술적 분석에서 매수 및 매도 압력을 측정하는 데 사용됩니다. 누적 지표로, 가격이 상승한 날에는 해당 일의 거래량이 누적 OBV 총합에 더해집니다. 가격이 하락한 날에는 해당 일의 거래량이 OBV 합계에서 차감됩니다. 그러면 OBV 값은 쉽게 해석할 수 있도록 선으로 표시됩니다. 잔고 거래량은 주로 전체 가격 추세를 확인하거나 식별하거나 다이버전스 후 가격 변동을 예측하는 데 사용됩니다.

  

역사

온밸런스 볼륨(OBV)은 조 그랜빌이 1963년 저서 <그랜빌의 주식시장 수익의 새로운 열쇠>에서 소개했습니다. 이 지표는 양수 및 음수 거래량 흐름을 설명하는 최초의 알려진 지표 중 하나이기 때문에 역사적으로 중요한 의미를 가집니다.

계산

온 밸런스 볼륨은 기술적 분석에서 가장 간단한 계산법 중 하나입니다. 몇 가지 조건에 따라 더하거나 빼기만 하면 됩니다.

1. 현재 종가가 이전 종가보다 큰 경우:

이전 OBV + 현재 거래량 = 현재 OBV

2. 현재 종가가 이전 종가보다 작으면 2:

이전 OBV - 현재 거래량 = 현재 OBV

3. 현재 종가가 이전 종가와 같으면:

이전 OBV = 현재 OBV

기본 사항

상승일의 거래량이 하락일의 거래량을 앞지르면 OBV가 상승합니다. 하락일의 거래량이 상승일의 거래량을 앞지르면 OBV는 하락합니다. 이는 본질적으로 OBV가 상승하면 매수 압력이 상승하고, OBV가 하락하면 매도 압력이 상승한다는 것을 의미합니다. 잔고 거래량 지표의 기본 이론은 거래량이 가격보다 우선한다는 것입니다. 이는 OBV를 몇 가지 다른 용도로 사용할 수 있기 때문에 중요합니다. 일반적인 추세 식별 또는 확인에 사용할 수 있습니다. 또한 다이버전스 이후 가격 변동을 예측하는 데 사용할 수도 있습니다.

살펴봐야 할 사항

추세 식별

온 밸런스 볼륨(OBV)은 전반적인 시장 추세를 식별하거나 확인하는 데 유용합니다. 이는 추세를 파악할 수 있어야 효과를 발휘할 수 있는 추가 신호에 의해 생성된 신호 또는 설정을 확인하는 데 유용할 수 있습니다. 또한 양수 또는 음수 거래량 흐름(매수 및 매도 압력)의 변동이 가격 변동에 선행한다는 이론에 따라 OBV는 잠재적 추세 반전도 식별할 수 있습니다.

다이버전스

다이버전스는 가격 변동이 지표에 의해 확인되지 않을 때 발생합니다. 많은 경우 이러한 차이는 잠재적 반전을 나타낼 수 있습니다. 특히 가격 변동에 앞서 양수 및 음수 거래량 변동이 선행된다는 OBV 지표의 전제를 고려할 때 더욱 그렇습니다.

강세 OBV 다이버전스는 가격은 하락하지만 OBV는 상승할 때 발생합니다.

약세 OBV 다이버전스는 가격이 상승하지만 OBV가 하락할 때 발생합니다.

요약

잔고 거래량 지표(OBV)는 매수 및 매도 압력을 측정하는 데 좋은 지표입니다. 많은 사람이 매수 및 매도 압력이 가격 변동에 선행한다고 믿기 때문에 이 지표는 가치가 있습니다. 특히 다이버전스는 현재 추세의 반전 가능성으로 항상 주목해야 합니다. 그러나 대부분의 지표와 마찬가지로 OBV는 추가 기술 분석 도구와 함께 사용하는 것이 가장 좋습니다.

## OBV (On-Balance Volume) 란 무엇입니까? 

거래량 균형(OBV)은 주식 거래량 흐름을 사용하여 주가의 변화를 예측하는 기술 거래 모멘텀 지표입니다. Joseph Granville은 1963년 저서 New Key to Stock Market Profits에서 처음으로 OBV 지표를 발표했습니다. Granville은 거래량이 시장의 핵심 원동력이라고 믿고 거래량 변화에 따라 시장의 주요 움직임이 발생할 때를 예측 할 수 있도록 OBV를 설계했습니다. Granville는 거의 저서에서 OBV에 의해 생성 된 예측을 "단단하게 감긴 스프링"이라고 설명했습니다. 그는 주가의 큰 변화없이 거래량이 급격히 증가하면 결국 가격이 상승하거나 하락할 것이라고 믿었습니다.

### OBV 추세 신호

- 가격과 OBV 모두 더 높은 정점과 더 높은 저점을 만들면 상승 추세가 계속 될 것입니다. 
- 가격이 계속해서 저점을 낮추고 OBV가 저점을 낮추지 못하면 하락 추세가 정체되거나 반등 할 가능성이 높습니다.이를 포지티브 다이버전스라고 합니다. 
- 거래 기간 동안 OBV가 상승하면 누적이 발생할 수 있습니다. 이는 상승 돌파에 대한 경고입니다. 
- 거래 기간 동안 OBV가 하락하면 분배가 발생할 수 있습니다. 이는 하락 돌파에 대한 경고입니다. 
- 가격이 계속해서 더 높은 피크를 만들고 OBV가 더 높은 피크를 만들지 못하면 상승 추세가 정체되거나 실패 할 가능성이 있습니다.이를 음의 발산이라고 합니다. 
- 가격이 계속해서 저점을 낮추고 OBV가 저점을 낮추지 못하면 하락 추세가 정체되거나 실패 할 가능성이 높습니다. 이를 양의 발산이라고 합니다.

## OBV 계산 방법

OBV는 다음 공식에 의해서 계산됩니다.    

![](https://blog.kakaocdn.net/dna/uf4dC/btqRnN9Xga0/AAAAAAAAAAAAAAAAAAAAAGOb6Qk0AwvX5pKAll045GOV0oE8efsCHSXLzJTiWlxu/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=ctZ4FkWfXxzJz7KmwZzBO5SDs5Q%3D)

## **OBV를 이용한 매수/매도 타이밍 전략** 

### **전략 #1** 

OBV를 사용하는 거래자는 거래 전략을 세우기 위해 OBV의 변화율에 관심을 가지는 경우가 있습니다. OBV가 상승 방향으로 움직이고 있다면 큰 주가 상승이 올 수 있다고 생각 할 수 있고, OBV가 하락 방향으로 움직이고 있다면 큰 주가 하락을 생각할 수 있습니다. 예를 들어, OBV가 해당 가격 변동보다 빠르게 하락하면 조만간 엄청나게 큰 가격 하락이 올 가능성이 있음을 알 수 있습니다.

### **전략 #2**

OBV에 이동 평균을 추가하여 주식을 매매 할 시기를 결정하고 교차점(Cross-over)을 신호로 거래할 수도 있습니다. 이것이 이번에 소개해 드릴 내용입니다.

> OBV가 지수 이동 평균 (EMA) 이상에서 거래를 시작하면 주식을 매수할 타이밍을 의미합니다.  
> OBV가 지수 이동 평균 (EMA) 아래에서 거래를 시작하면 주식을 매도할 타이밍을 의미합니다.

참고 : OBV의 장기 이동 평균으로 100일 기간 지수 이동 평균을 추가하면 단기 이동 평균보다 더 효과적입니다. 200 지수 이동 평균은 매수/매도 타이밍을 조금 더 적게 산출해 줍니다. OBV에서 매수/매도 타이밍을 Whipsaw라고 하는데, 이는 특정 시간에 유가 증권의 가격이 한 방향으로 움직이다가 반대 방향으로 빠르게 움직일 때를 의미하며 주식의 매수와 매도에 대한 거래량의 움직임을 설명해 줍니다.

## **OBV 전략의 요점** 

OBV는 거래량이 늘어난 날과 내려간날의 단순 누적 합계입니다. OBV가 가격과 함께 움직이면 현재 추세와 동행하고 있음을 알 수 있습니다. OBV와 가격 사이의 차이가 발생한다면 주가 흐림이 반전 될 수 있음을 의미합니다. 추세선을 사용하면 OBV와 가격 흐림에 차이가 발생하는지 파악하여 거래 기회를 획득하는데 도움이 될 수 있습니다. OBV는 가격 변화 방향을 예측하는데도 도움이 됩니다. OBV를 이용함에 있어 주의해야 할 점이 있습니다. 가령, 어떤 특별한 이유 없이 거래량이 급증하는 경우가 있는데, 이런 경우에는 지표가 왜곡되어 객관적인 해석을 더 어려워 지기도 합니다. 또한 OBV가 종종 가격을 선도하는 것처럼 보일 수 있지만, 이것은 종종 우리가 찾고자 하는 증거를 검색하는 경우입니다. 따라서 OBV는 가격 분석과 함께 활용될 수 있는 지표지만 전적으로 OBV에 의존해서 투자전략을 세우기에는 한계가 있습니다.

- OBV는 가격 예측을 위해 거래량의 변화를 사용하는 기술적 지표입니다. 
- OBV는 해당 종목에 반영된 강세 또는 약세에 대한 군중 심리를 보여줍니다. 
- 가격과 OBV 간의 상대적인 추세 흐름을 비교하면, 주식 차트 하단에서 띄워놓고 보는 (빨간색 또는 초록색으로 표시되는) 거래량 히스토그램 보다 더 많은 정보를 알 수 있습니다.

## **파이썬을 이용한 OBV 투자 전략**

파이썬을 이용해서 OBV를 계산하고, 이를 기반으로 투자 전략을 세워보겠습니다. 우선 분석이 필요한 라이브러리를 Import 하겠습니다.

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
plt.style.use('fivethirtyeight')
```

## **주식 데이터 불러오기**

실습에 사용하게될 예제로 코로나19 백신 개발 업체로 잘 알려진 아스트라제네카(NYSE: AZN) 데이터를 사용하겠습니다. 야후 파이낸스에서 데이터를 가져오려면 yfinance 라이브러리가 필요합니다. yfinance 라이브러리가 없다면, '!pip install yfinance'를 통해서 설치해주세요.

```
import yfinance as yf
df = yf.download('AZN', start="2018-12-01", end="2020-11-30")
df['Date'] = df.index
df.head()
```

![](https://blog.kakaocdn.net/dna/b9zCYT/btqReRstpCf/AAAAAAAAAAAAAAAAAAAAANtkS7n6IwXO6c6XJnURoUNgmXldeBUJRNKxfJlLINIq/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=7OhXD9%2BUOyC0umcehGPvoCEM%2FgU%3D)

## **주가 데이터 시각화**

아래 파이썬 코드를 이용하여 yfinance에서 불러온 주가 데이터를 시각화 해보겠습니다.

```
# Create and plot the graph
plt.figure(figsize=(12.2,4.5)) #width = 12.2in, height = 4.5
plt.plot( df['Close'],  label='Close')#plt.plot( X-Axis , Y-Axis, line_width, alpha_for_blending,  label)
plt.xticks(rotation=45) 
plt.title('Close Price History')
plt.xlabel('Date',fontsize=18)
plt.ylabel('Price USD ($)',fontsize=18)
plt.show()
```

![](https://blog.kakaocdn.net/dna/bF0iH7/btqRheUZT0f/AAAAAAAAAAAAAAAAAAAAAA_oTKBzX1FOhsofTBGebbmCoAWApsJnRrrRtFWNo3y_/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=5Tzutjotf87uNerHcqJyYZ0%2BI84%3D)

## **OBV 계산하기**

```
#Calculate the On Balance Volume
OBV = []
OBV.append(0)
for i in range(1, len(df.Close)):
    #If the closing price is above the prior close price 
    if df.Close[i] > df.Close[i-1]: 
        #then: Current OBV = Previous OBV + Current Volume
        OBV.append(OBV[-1] + df.Volume[i]) 
    elif df.Close[i] < df.Close[i-1]:
        OBV.append( OBV[-1] - df.Volume[i])
    else:
       OBV.append(OBV[-1])
```

## **OBV와** **지수 이동 평균을 새로운 컬럼에 추가하기**

```
# OBV값을 pd.DataFrame의 새로운 컬럼에 추가 
df['OBV'] = OBV

# 지수 평균 이동값 계산
df['OBV_EMA'] = df['OBV'].ewm(com=20).mean()

# 데이터 출력
df
```

![](https://blog.kakaocdn.net/dna/6jdpe/btqRoRD08QY/AAAAAAAAAAAAAAAAAAAAAH0SdNSiwKk5yYhJO_27lxvmPmYKbFn3JKxzOQohadB2/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=jWh3yYE5jCfuJiD8Skerb%2FS3igo%3D)

## **OBV와 OBV의 지수 이동 평균값 시각화**

```
#Create and plot the graph
plt.figure(figsize=(12.2,4.5)) #width = 12.2in, height = 4.5
plt.plot( df['OBV'],  label='OBV', color= 'orange')
plt.plot( df['OBV_EMA'],  label='OBV_EMA', color= 'purple')
plt.xticks(rotation=45) 
plt.title('OBV/OBV_EMA')
plt.xlabel('Date',fontsize=18)
plt.ylabel('Price USD ($)',fontsize=18)
plt.show()
```

![](https://blog.kakaocdn.net/dna/ohVEq/btqRigrABTU/AAAAAAAAAAAAAAAAAAAAAPgO9J0t3PlSubuZNS5mxD6hvtrzSVmjXMrSQB0i3FL8/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=sRKeeCYCYB6itXHkdS1Xg03gmT8%3D)

## **매수/매도 타이밍 신호 찾는 함수 생성**

- 매수 신호: OBV > OBV_EMA
- 매도 신호: OBV < OBV_EMA

```
def buy_sell(signal, col1, col2):
  sigPriceBuy = []
  sigPriceSell = []
  flag = -1 #A flag for the trend upward/downward

  #Loop through the length of the data set
  for i in range(0,len(signal)):

    #if OBV > OBV_EMA  and flag != 1 then buy else sell
      if signal[col1][i] > signal[col2][i] and flag != 1:
          sigPriceBuy.append(signal['Close'][i])
          sigPriceSell.append(np.nan)
          flag = 1

      #else  if OBV < OBV_EMA  and flag != 0 then sell else buy
      elif signal[col1][i] < signal[col2][i] and flag != 0:    
          sigPriceSell.append(signal['Close'][i])
          sigPriceBuy.append(np.nan)
          flag = 0

      #else   OBV == OBV_EMA  so append NaN 
      else: 
        sigPriceBuy.append(np.nan)
        sigPriceSell.append(np.nan)

  return (sigPriceBuy, sigPriceSell)
```

## **매수/매도 신호값을 새로운 컬럼에 추가**

```
x = buy_sell(df, 'OBV','OBV_EMA' )
df['Buy_Signal_Price'] = x[0]
df['Sell_Signal_Price'] = x[1]
#Show the data frame
df
```

![](https://blog.kakaocdn.net/dna/bZdlcQ/btqRoQrCsQR/AAAAAAAAAAAAAAAAAAAAALTDOOeKrgeMbevEbw-duGJpsBAReBFm02CcrYD--n_B/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=38hWOA9VjQ8M4T8SFAvH6ci7gLs%3D)

## **매도/매도 신호 시각화**

```
# Create and plot the graph
plt.figure(figsize=(12.2,4.5)) #width = 12.2in, height = 4.5
plt.scatter(df.index, df['Buy_Signal_Price'], color = 'green', 
                    label='Buy Signal',  marker = '^', alpha = 1)
plt.scatter(df.index, df['Sell_Signal_Price'], color = 'red',
                    label='Sell Signal', marker = 'v', alpha = 1)
plt.plot( df['Close'],  label='Close Price', alpha = 0.35)
plt.xticks(rotation=45)
plt.title('The Stock Buy / Sell Signals')
plt.xlabel('Date',fontsize=18)
plt.ylabel('Close Price USD ($)',fontsize=18)
plt.legend( loc='upper left')
plt.show()
```

![](https://blog.kakaocdn.net/dna/b4xrX3/btqRnNa1ErW/AAAAAAAAAAAAAAAAAAAAAEwmWZri5Izvk-S7nXfZsWeLvxMZXlie9P0POQ0H4sAB/img.png?credential=yqXZFxpELC7KVnFOS48ylbz2pIh7yKj8&expires=1777561199&allow_ip=&allow_referer=&signature=Xg9Yarss0mhAKQ1tc63B8uh80A0%3D)

그래프를 살펴보면 OBV를 이용한 투자 전략이 어느정도 잘 작동하는 것 같습니다. 즉, 이 데이터 세트에 이 전략을 사용했다면, 이 기간 내에 수익을 올렸을 것입니다. 그러나 이 지표가 완벽하지 않으며 전략이 성공을 보장하지 않는다는 점을 명심하십시오. 이 전략을 사용하기 전에 더 많은 테스트를 수행해야하며 주식을 매매 할시기에 대한 자세한 정보를 위해 OBV 전략과 함께 다른 지표를 함께 사용하시길 권장드립니다.

참고) 이 글은 randerson112358의 Know When To Buy and Sell Stock Using A Trading Strategy With On-Balance Volume (OBV) and Python을 각색하여 한글로 번역한 글입을 밝힙니다. 원문은 [링크](https://randerson112358.medium.com/stock-trading-strategy-using-on-balance-volume-obv-python-77a7c719cdac)를 통해서 확인하실 수 있습니다.