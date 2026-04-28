# [기술적분석] Stochastic 알고리즘 및 매매 시그널
- 분류 : 모멘텀
- 나의 메모: 이 자료는 종목의 단기/중기 매매 타이밍을 결정하기 위한 수학적 지표야.
`wiki/기술적분석/` 폴더를 새로 만들고, 그 안에 `모멘텀.md` 파일을 생성해 줘. AI가 나중에 주가 데이터를 입력받았을 때 기계적으로 매수/매도를 판정할 수 있도록, 이 지표의 계산 산식(Logic)과 정확한 '매수 조건(Trigger)' 및 '매도 조건'을 불릿 포인트로 수치화해서 명시해 줘.

---

## **1. 개요**

  

**스토캐스틱 패스트(Stochastic Fast)**는 일정 기간 동안의 최고가와 최저가의 범위 중에서 현재 가격의 위치를 백분율로 나타내는 기술적 지표이다. **주가가 과열 구간에 들어서게 되면 조만간 하락**하고 반대로 **주가가 침체 구간에 들어서게 되면 조만간 반등**하는 속성을 반영하고 있다.

  

  

#### **1-1. 배경**

정식 명칭은 스토캐스틱 오실레이터(Stochastic Oscillator)로, 1950년년대 조지 레인(George C. Lane)에 의해 고안되었다. 주가 추세의 변화속도를 설명하는 모멘텀은 가격이 변하기 전에 미리 바뀌는 성질을 가진다. 이러한 성질을 이용하여, 스토캐스틱을 모멘텀 지표로써 주가의 변화를 예측하는 도구로 개발하였다.

  

![](https://file.alphasquare.co.kr/media/images/timeline/c84ad178882a4f15a029c4d409a88a6b.png)

  

  

## **2. 산출법**

스토캐스틱 패스트를 구성하는 두 가지 지표인 %K와 %D는 다음과 같이 계산 할 수 있다.

  

![](https://file.alphasquare.co.kr/media/images/timeline/f69ee1256d03484da70d588dec7b20e6.png)

  

#### **2-1. 변수**

![](https://file.alphasquare.co.kr/media/images/timeline/481c5ab85a324a99b7203848345b8b2e.png)

  

- **기간(%K)** : 최고가와 최저가를 산출하는 기간을 정하기 위해 쓰이는 N에 해당하는 값이다. 기본 값은 14일이며, 5일~ 30일 사이의 값이 적절하다.
- **기간(%D)** : %K의 이동평균을 구하는 기간을 정하기 위해 쓰이는 M에 대응하는 값이다. 기본 값은 3일이며, 3일~10일 사이의 값이 적절하다.

  

  

## **3. 분석**

#### **3-1. %K와 %D의 관계**

💡 **%D는 %K의 M일 간의 이동 평균을 계산한 값**이다.

**%K**

스토캐스틱에서 %K는 당일 종가와 최근 N일간의 최저가의 차이를 최근 N일간의 최고가와 최저가의 차로 나눈 백분율 값이다. 따라서 이 값은 0%과 100%사이를 움직이는데, 100%에 가까울 수록 매수세가 강하다는 것을 의미하며, 0%에 가까울수록 매도세가 강하다는 것을 의미한다.

**%D**

%D는 %K의 M일 간의 이동 평균을 계산한 값으로, M일 간의 %K의 총합을 M으로 나눈 값이다. %D는 평균값이기 때문에 %K보다 움직임이 느린 성질이 있다.

  

  

#### **3-2. 다른 지표와의 연관성**

💡 **스토캐스틱 패스트와 관련된 지표로는 스토캐스틱 슬로우, RSI 등이 있다.**

[**스토캐스틱 슬로우** (Stochastic Slow](https://alphasquare.oopy.io/board/technical-indicator/stochastic-slow))

- 스토캐스틱 패스트는 파동이 심하다는 단점이 있다. 이를 보완하기 위해 스토캐스틱 패스트의 이동평균을 계산하여 표시한 스토캐스틱 슬로우라는 지표를 사용한다.

[**RSI**](https://alphasquare.oopy.io/board/technical-indicator/rsi) (Relative Strength Index, 상대강도지수)

- RSI는 스토캐스틱 패스트와 계산 방법과 그래프의 형태가 비슷하며, 다이버전스(Divergence)를 응용한 기법이 자주 사용된다.

  

  

#### **3-3. 한계**

💡 스토캐스틱 패스트는 파동이 심해 잦은 매매 신호가 나타나기 때문에 이동평균선과 MACD 와 같은 추세지표 등 다른 보조지표와 함께 종합적으로 판단하는 것이 효과적이다.

스토캐스틱 패스트는 파동이 심하기 때문에 **약간의 파동에도 다이버전스가 발생하거나 잦은 매매신호**가 나타난다. 이는 손실의 누적을 유발할 수 있다. 또한 횡보장이나 박스권장세 같이 추세가 약한 시점에서는 적중률이 높지만 추세가 형성된 장에서는 그렇지 않다는 단점이 있다.

  

  

## **4. 활용**

#### **4-1. 과매수/과매도 (Overbought / Oversold)**

💡 **%K 선이 20 아래에 있다면 과매도, 80 위에 있다면 과매수 구간으로 파악할 수 있다.**

![](https://file.alphasquare.co.kr/media/images/timeline/bbcee69f77f8449cbac34b543d2589b9.png)

일반적으로 %K선이 20 아래에 있다면 과매도 구간, 80 위에 있다면 과매수 구간으로 본다. 따라서 **스토캐스틱이 과매도선을 상향 돌파하면 매수신호**, **과매수선을 위에서 아래로 돌파하면 매도신호**를 나타낸다. 다만, 과매도선과 과매수선을 이용한 매수신호는 횡보 장세에서는 잘 적용되지만, 추세가 형성된 후에는 그렇지 못한 경우가 많다.

🐥 [차트게임에서](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast) [과매수/과매도를 활용한 매매법](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast) [연습하러가기](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast)

  

  

#### **4-2. %K-%D 교차**

💡 **스토캐스틱 패스트의 %K와 %D가 교차하는 시점을 매매신호로 활용할 수 있다.**

![](https://file.alphasquare.co.kr/media/images/timeline/98f206bd3eec4db68535451877097ccf.png)

**%K값이 %D 값을 상향 돌파하는 골든 크로스가 생성되면 매수신호**, **반대로 하향 돌파하는 데드 크로스가 생성되면 매도신호**로 해석할 수 있다. 다만 스토캐스틱은 변동성이 크다는 특징이 있기 때문에, 설정하는 기간에 따라 잦은 매매신호가 발생할 수 있다.

🐥 [차트게임에서](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast) [%K-%D를 활용한 매매법](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast) [연습하러가기](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast)

  

  

#### **4-3. Stochastic Pop**

💡 **모멘텀을 이용한 단기매매 기법인 스토캐스틱 팝 전략에 활용할 수 있다.**

관성의 법칙과 마찬가지로, 가격도 물체와 같이 한 번 움직이면 같은 방향으로 진행하려는 성질이 있다. 그렇기 때문에 과매수, 과매도 구간에서도 가격이 곧바로 바뀌지 않고 한동안 그 범위내에서 진행된다는 성질을 지니고 있다.

Stochastic Pop은 이러한 성질을 이용한 전략으로, 기술적 분석가인 Jake Bernstein이 제시하였다. 주로 5분봉, 30분봉과 같이 단기매매에서 응용되는 전략으로, 매매 규칙은 다음과 같다(선물거래에 사용된 트레이딩 기법이기 때문에, 공매도를 포함한 진입과 청산을 고려한다).

  

**진입 조건**

✅ %K가 80선을 상향 돌파하면 매수한다(롱 포지션 진입).

✅ %K가 20선을 하향 돌파하면 공매도한다(숏 포지션 진입).

**청산 조건**

✅ %K가 80선을 하향 돌파하거나, %K가 %D를 하향 교차하면 매도한다(롱 포지션 청산).

✅ %K가 20선을 상향 돌파하거나, %K가 %D를 상향 교차하면 매수한다(숏 포지션 청산).

🐥 [차트게임에서](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast) [Stochastic Pop 전략](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast) [연습하러 가기](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast)

  

  

#### **4-4. 다이버전스 (Divergence)**

💡 **스토캐스틱 패스트의 흐름과 주가 추세가 역전되는 상황이 발생한다면, 추세 전환의 신호로 해석될 수 있다.**

![](https://file.alphasquare.co.kr/media/images/timeline/a0da7a9bdf0a47ce9a624b5f47eda4e9.png)

  

**다이버전스는 현재 주가 추세와 보조지표의 흐름이 역전되는 형상**으로, 가격은 오르는데 보조지표는 내려가는 경우 혹은 가격은 내려가는데 보조지표는 오르는 경우를 의미한다. 현재 가격과 %K선 사이에 다이버전스가 발생할 경우 추세의 전환이 발생할 것이라는 신호로 해석할 수 있다.

  

Bull & Bear 다이버전스는 이러한 다이버전스의 예시 중 하나로, Bull & Bear Set-up이라고도 불린다. Bear Set-up은 가격의 저점은 높아지는데 스토캐스틱의 저점은 낮아지는 현상이다. 반대로 Bull Set-up은 가격의 고점은 낮아지는데 %D의 고점은 높아지고 있는 현상을 뜻한다.

  

**Bear Set-up이 나타나면 곧 이어 나타나는 고점은 의미 있는 고점이 될 가능성이 높아 매도 기회를 포착하는 전략**으로 사용될 수 있으며, **Bull Set-up이 나타나면 곧 이어 나타나는 저점은 의미있는 저점이 될 가능성이 높아 매수 기회를 포착하는 전략**으로 사용할 수 있다.

🐥 [차트게임에서](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast) [다이버전스 활용 매매법](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast) [연습하러가기](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast)

  

  

#### **4-5. Hinge**

💡 **스토캐스틱 패스트의 기울기가 급격히 감소되며 움직임이 둔화되는 경우 가격 추세가 전환될 수 있다.**

![](https://file.alphasquare.co.kr/media/images/timeline/233fc592216e4c509d2a5faf45f9f917.png)

  

Hinge는 스토캐스틱의 움직임이 둔화되는 패턴을 뜻한다. %K나 %D의 기울기는 가격이 움직이는 속도로 파악할 수 있기 떄문에 급격히 기울기가 감소되며 움직임이 둔화되는 경우는 가격방향이 조만간 전환될 수 있음을 나타낸다. 다만 신뢰도가 낮은 편이기 때문에 다른 패턴과 병행하여 보는 것이 좋다.

🐥 [차트게임에서](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast) [Hinge 활용 매매법](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast) [연습하러 가기](https://alphasquare.co.kr/chart-game/guest?utm_source=oopy&utm_medium=text&utm_campaign=technical-indicators&content=stochastic-fast)

  

####   

#### **4-6. Knee & Shoulder**

💡 **Knee & Shoulder 패턴 발생 시 추세 전환의 신호로 해석할 수 있다.**

차트에서 가격의 고점이나 저점이 뾰족한 형태로 반전하는 현상을 스파이크(spike)라고 일컫는다.

Knee & Shoulder은 %K에서 스파이크 현상이 일어난 이후 한 번 더 일어나는 스파이크가 %D와 작은 차이로 교차하지 못하고 추세가 변하는 패턴을 말한다.

그 중 Knee는 차트가 아래로 볼록할 때를 의미하며, Shoulder은 차트가 위로 볼록할 때를 의미한다. Knee & Shoulder 패턴이 발생할 경우, 추세전환이 되었다고 해석할 수 있다.

  

![](https://file.alphasquare.co.kr/media/images/timeline/11e08b50ce3d41a896da472409c32016.png)

![](https://file.alphasquare.co.kr/media/images/timeline/9fbb8ad01ac2470192bf27374f933c1d.png)> 스토캐스틱(stochastic)

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfODkg/MDAxNTk2NTQwMjQzNTk0.-2bEmhw4gzipIHeJOaIYCU9bLfCtAPT3jJthrRhMgXUg.SKW8A0NeaiT-qfaCfwV9hQAI42smzOLBy4r-ECCEHrwg.PNG.rmsgud2007/1.png?type=w800)

​

**주가는** 많이 오르게 되면 일정 기간 조정을

받고 많이 하락하게 되면 저평가된 주식에

대한 매수심리가 강해져 오르는 특성상

**물결무늬의 파동을 그리며 나아가는 성격**을

가지고 있습니다!

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjk1/MDAxNTk2NTQwMzg1MjQ0.g1sR50Na7PyQoXNEipyFYefL7ZoJunWP7mqjoU5AChIg.rq2n2U7IYFm8sw2EKZYy3Cy9hEsRlEKW-LjJaLMgL8Mg.PNG.rmsgud2007/%EC%82%BC%EC%84%B1%EC%A0%84%EC%9E%90.png?type=w800)

이처럼 주식은 항상 파동을 그리며

앞으로 나아가는데 여기서 **스토캐스틱**이란

**최근 n일간의 최고가와 최저가의 범위**

**내에서 현재 가격의 위치를 백분율로**

**표시하여 현 주가의 추세를 예측**하는

지표입니다!

​

저도 수년째 쓰고 있는 지표고 이 지표는

무려 70년의 역사를 자랑할 만큼

투자자들 사이에서 널리 알려져 있는

보조지표 중 하나입니다.

​

스토캐스틱(stochastic)은 **Fast**와 **Slow**로

나뉘게 되는데 사실 Stochastic Fast는

주가에 굉장히 민감하게 반응하기 때문에

실제 매매에 적용하기란 굉장히 까다롭고

**실전 매매에서는 저뿐만 아니라 많은**

**투자자들이 Stochastic slow를 사용**합니다.

​

먼저 실제 차트에 보조 지표를 설정하는

방법부터 설명드리겠습니다.

​

> 스토캐스틱(stochastic Slow)
> 
> 설정하는 방법

저는 삼성증권을 쓰고 있지만

다른 증권사 hts를 사용하셔도 설정 방법은

거기서 거기라 큰 차이는 없습니다.. ㅋㅋ

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMzcg/MDAxNTk2NTQwOTk3MDg2.gBvxyguMI8KJBkWu7zZHacvEajCahwpN163BJlM6xsYg.vnak42G4NBTxL2u2YmbzyHBo9EF_dC4dkBFGOrACJrMg.PNG.rmsgud2007/%EC%A7%80%ED%91%9C%EC%84%A4%EC%A0%95.png?type=w800)

hts 차트에서 마우스 우 클릭을 하신 다음

**'지표 설정'**을 들어가줍니다.

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjA0/MDAxNTk2NTQxMTAxMzY3.Hg1rNzvwxvAyLEDR30X_C9RA9yK4K_-VfBFwcwJKVQ4g.W5lAKqdLi-e6iC-frxLDoQJquaVZd2nZEvOS6WMVvlsg.PNG.rmsgud2007/%EC%B6%94%EA%B0%80.png?type=w800)

먼저 좌측 상단에 **'추세 지표'**를 눌러주시고

아래에 있는 박스를 뒤지다 보면

**'Stochastic Slow'**가 있으니 추가 버튼을

눌러줍니다.

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjQ0/MDAxNTk2NTQxMjcwMTE1.0_RuO1peIp80CaJAtVhv3S7UIITSzVBYJU2ukai4bnIg.dTDMYh3PPrevCJt3dqdKKfBq0zutN8I-AzmPFONFFygg.PNG.rmsgud2007/%EA%B5%AC%EA%B0%84.png?type=w800)

사용 지표란에 Stochastic Slow가

추가된 게 보이시나요?

​

눌러주시면 **%K, %D, 구간 설정, 기준선**

등등 어려운 말들이 나오니 일단 무시하고

확인 버튼을 눌러줍시다!

​

백분율이 어쩌고저쩌고 다 해도

설정만 해놓으면 hts가 알아서 계산해 주니

큰 신경 안 쓰셔도 됩니다.. ㅋㅋㅋㅋㅋ

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMTY1/MDAxNTk2NTQxNTA0Mzk3.oHyoVCw-UwinY0DcFib4elYli3o0EI6HWUFcw5AMt0kg.2-3dwAUzlnrX9SxvRV-jlXsvIiorj59oCNOQcdg5QXYg.PNG.rmsgud2007/%EC%8A%A4%ED%86%A0.png?type=w80_blur)

​

거래량 밑에 이상하게 생긴 곡선들이

생긴 게 보이시나요?

이 스토캐스틱을 실전 매매에 활용하는

방법을 설명드리겠습니다.

​

> 스토캐스틱(Stochastic Slow)
> 
> 활용 방법

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfNzAg/MDAxNTk2NTQxNzk2NDM2.UtGg8Vu60HTstIf2Dl-VxRTnC65WTyig6y1Sg6HUlUkg.9a3Mv2SSXdZnLwGVwI75Gzq8KTO4oi_yk3xry9qVrrog.PNG.rmsgud2007/%EB%B3%B4%EB%8A%94%EB%B2%95.png?type=w80_blur)

**스토캐스틱 지표를 보는 방법은**

**크게 두 가지로 나뉩니다.**

​

보라색 동그라미로 색칠된 ​**과매수**

**구간과 과매도 구간을 활용한 방법**과

회색 동그라미로 표시된 **%K, %D 선을**

**활용한 방법**이 있습니다.

​

참고로 갈색선이 %K, 초록색 선이 %D,

과매수 구간이 빨간색, 과매도 구간이

파란색인데 이는 원하시는 색깔로

마음껏 바꾸셔도 상관없고 본인이 이것저것

만져보신 후 최적의 값을 찾아내 매매에

임하셔도 됩니다.

​

**비밀인데**

**저는 계산 값을 10, 5, 3으로 일봉이 아닌**

**주봉을 보는데 사용합니다 깔깔!**

> 과매수, 과매도 구간 활용

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMTk3/MDAxNTk2NTQyMDU5MDM5.g4RIVdn14LdL-beGP093EmIKjaMBj13DjRv7f5G8vBsg.7uo9CiNi_XhiFD_QTtBigvUVV9ZL8mCtbOZJxmszjMUg.PNG.rmsgud2007/%ED%99%9C%EC%9A%A9.png?type=w80_blur)

일반적으로 스토캐스틱 수치가 **80% 이상**일

경우에는 많은 투자자들이 매수하여 주가가

오른 상황이기 때문에 **'과매수 구간'**이라

부르고 반대로 **20% 미만**일 경우에는

**'과매도 구간'**이라고 부릅니다.

​

갈색깔의 %K 선이 과매도 구간에서

뚫고 나가는 **골든크로스 시점이**

**매수 시점**입니다.

​

처음이신 분들은 무슨 말인지

헷갈릴 수도 있으니 차트를 보면서

설명드리겠습니다!

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfOTcg/MDAxNTk2NTQyNDY5MTk1.3Le_z2NE4G2lKMdMmTykRwE4KXkHhj0J4wn6s54CUbMg.vmmrqDWMgO50RUqjsciI4UcVOqpi-6wAxGoBev74qo0g.PNG.rmsgud2007/%EC%83%81%EC%8A%B9.png?type=w80_blur)

갈색의 **%K 선이 과매도 구간을**

**뚫고 나간 이후 주가가 상향**하는 것이

보이시나요?

​

물론 반대로 과매수 구간에서

뚫고 내려가는 시점이 매도 시점이라

부르는데 동일한 차트를 보면서

설명드리겠습니다.

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjE5/MDAxNTk2NTQyNjk4MDgx.XyyK9sEUHa3JAShpl3vKt8_5xEaFUvLQzv7SjA2vzbIg.5VedkLQPxuRH_06elV8gayv1bIhAqop1pF6Doolb420g.PNG.rmsgud2007/%ED%95%98%EB%9D%BD.png?type=w800)

**%K 선이 과매수 구간에서**

**빠져나와 내려가는 동시에 주가가**

**하락**하는 모습을 볼 수 있는데

빠져나오는 시점이 바로 **매도 시점**입니다.

​

> %K 선과 %D 선을
> 
> 활용한 매매 방법

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMyAg/MDAxNTk2NTQyOTEwMzE1.cFMM0FezNgdXrtyXRprSZMeXineEXcIDM3lI0tPzq8cg.3DoO3LXQRC0XYPAVmUT2-YebfP6gxYKdbfAgR7iQIjYg.PNG.rmsgud2007/%EC%83%89.png?type=w800)

앞서 말씀드렸듯이

갈색선이 %K, 녹색선이 %D인데

%K 선이 %D 선을 뚫고 올라가는

**골든크로스 시점이 매수 타이밍이고**

**뚫고 내려가는 시점이 매도 타이밍입니다.**

​

말로만 설명하면 어려우니 이번에도

차트를 보면서 설명드릴게요.

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMTc4/MDAxNTk2NTQzMjk2NjQ0.IDekYRbd8bCxHzbjxyISrGotaNRb7ijv-Y4fya44_DMg.Rs52-TI1yQc0MVduJtuwF8sFKhjLnf_6a2jJJwF4Ebwg.PNG.rmsgud2007/%EC%98%A4%EB%A6%84.png?type=w800)

동그라미로 표시한 부분이 **%K 선이**

**%D 선을 뚫고 올라가는 골든크로스**

**시점**이며 이 시점부터 주가는 오르는 것을

확인할 수 있습니다.

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjU5/MDAxNTk2NTQzMzMyMDM3.QbhoMpvFnJqdYiXnxeRUOGLDRgx75XOkyr3AvM1_NIUg.QV3CoU2nKp1ECw0Z1aMiU3wuJ-1P2LgLspm4xVUNuCsg.PNG.rmsgud2007/%EB%82%B4%EB%A6%BC.png?type=w800)

반대로 **%K 선이 %D 선을 뚫고 내려가는**

**데드크로스 시점**과 함께 주가는

떨어지는 모습을 볼 수 있는데 이 시점이

매도 타이밍이라고 보시면 됩니다.

​

과매수 구간, 과매도 구간을 활용한

방법과 %K선, %D 선을 활용한 방법을

제외하고도 잘 사용하지 않는 방법이지만

기준선을 활용한 매매 방법도 있습니다.

​

포스팅하려던 계획에는 없었지만

이왕 포스팅하는 김에 기본적인

개념 정도만 알려드리겠습니다!

> 기준선을 활용한
> 
> 매매 방법

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjkg/MDAxNTk2NTQzNTg3ODEx.UjEjz9PutbyH0AFQr2LjEN41tAj7N42N9cZ5qNn3IEEg.8XJHRIf-TL76kzwomY-COLrh1fqazJma5DG9LWNTrqMg.PNG.rmsgud2007/%EA%B8%B0%EC%A4%80%EC%84%A0.png?type=w800)

우측에 보시면 0%부터 100%까지

있는 게 보이시나요?

​

일반적으로는 **50% 선을 기준**으로 하고

%K 선과 %D 선이 기준선 아래에서

**상향 돌파하는 시점이** **매수 시점****,**

**하향 돌파하는 시점이** **매도 시점****입니다.**

---

%K, %D, 기준선에 사용되는 값은

임의대로 설정하셔도 좋습니다만

보조 지표는 보조 지표일 뿐 이것만 믿고

투자하시면 큰일 납니다..!

​

투자는 항상 신중하게!

​

오늘도 유익한 포스팅이었으면

좋겠습니다.

> 스토캐스틱(stochastic)

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfODkg/MDAxNTk2NTQwMjQzNTk0.-2bEmhw4gzipIHeJOaIYCU9bLfCtAPT3jJthrRhMgXUg.SKW8A0NeaiT-qfaCfwV9hQAI42smzOLBy4r-ECCEHrwg.PNG.rmsgud2007/1.png?type=w800)

​

**주가는** 많이 오르게 되면 일정 기간 조정을

받고 많이 하락하게 되면 저평가된 주식에

대한 매수심리가 강해져 오르는 특성상

**물결무늬의 파동을 그리며 나아가는 성격**을

가지고 있습니다!

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjk1/MDAxNTk2NTQwMzg1MjQ0.g1sR50Na7PyQoXNEipyFYefL7ZoJunWP7mqjoU5AChIg.rq2n2U7IYFm8sw2EKZYy3Cy9hEsRlEKW-LjJaLMgL8Mg.PNG.rmsgud2007/%EC%82%BC%EC%84%B1%EC%A0%84%EC%9E%90.png?type=w800)

이처럼 주식은 항상 파동을 그리며

앞으로 나아가는데 여기서 **스토캐스틱**이란

**최근 n일간의 최고가와 최저가의 범위**

**내에서 현재 가격의 위치를 백분율로**

**표시하여 현 주가의 추세를 예측**하는

지표입니다!

​

저도 수년째 쓰고 있는 지표고 이 지표는

무려 70년의 역사를 자랑할 만큼

투자자들 사이에서 널리 알려져 있는

보조지표 중 하나입니다.

​

스토캐스틱(stochastic)은 **Fast**와 **Slow**로

나뉘게 되는데 사실 Stochastic Fast는

주가에 굉장히 민감하게 반응하기 때문에

실제 매매에 적용하기란 굉장히 까다롭고

**실전 매매에서는 저뿐만 아니라 많은**

**투자자들이 Stochastic slow를 사용**합니다.

​

먼저 실제 차트에 보조 지표를 설정하는

방법부터 설명드리겠습니다.

​

> 스토캐스틱(stochastic Slow)
> 
> 설정하는 방법

저는 삼성증권을 쓰고 있지만

다른 증권사 hts를 사용하셔도 설정 방법은

거기서 거기라 큰 차이는 없습니다.. ㅋㅋ

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMzcg/MDAxNTk2NTQwOTk3MDg2.gBvxyguMI8KJBkWu7zZHacvEajCahwpN163BJlM6xsYg.vnak42G4NBTxL2u2YmbzyHBo9EF_dC4dkBFGOrACJrMg.PNG.rmsgud2007/%EC%A7%80%ED%91%9C%EC%84%A4%EC%A0%95.png?type=w800)

hts 차트에서 마우스 우 클릭을 하신 다음

**'지표 설정'**을 들어가줍니다.

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjA0/MDAxNTk2NTQxMTAxMzY3.Hg1rNzvwxvAyLEDR30X_C9RA9yK4K_-VfBFwcwJKVQ4g.W5lAKqdLi-e6iC-frxLDoQJquaVZd2nZEvOS6WMVvlsg.PNG.rmsgud2007/%EC%B6%94%EA%B0%80.png?type=w800)

먼저 좌측 상단에 **'추세 지표'**를 눌러주시고

아래에 있는 박스를 뒤지다 보면

**'Stochastic Slow'**가 있으니 추가 버튼을

눌러줍니다.

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjQ0/MDAxNTk2NTQxMjcwMTE1.0_RuO1peIp80CaJAtVhv3S7UIITSzVBYJU2ukai4bnIg.dTDMYh3PPrevCJt3dqdKKfBq0zutN8I-AzmPFONFFygg.PNG.rmsgud2007/%EA%B5%AC%EA%B0%84.png?type=w800)

사용 지표란에 Stochastic Slow가

추가된 게 보이시나요?

​

눌러주시면 **%K, %D, 구간 설정, 기준선**

등등 어려운 말들이 나오니 일단 무시하고

확인 버튼을 눌러줍시다!

​

백분율이 어쩌고저쩌고 다 해도

설정만 해놓으면 hts가 알아서 계산해 주니

큰 신경 안 쓰셔도 됩니다.. ㅋㅋㅋㅋㅋ

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMTY1/MDAxNTk2NTQxNTA0Mzk3.oHyoVCw-UwinY0DcFib4elYli3o0EI6HWUFcw5AMt0kg.2-3dwAUzlnrX9SxvRV-jlXsvIiorj59oCNOQcdg5QXYg.PNG.rmsgud2007/%EC%8A%A4%ED%86%A0.png?type=w80_blur)

​

거래량 밑에 이상하게 생긴 곡선들이

생긴 게 보이시나요?

이 스토캐스틱을 실전 매매에 활용하는

방법을 설명드리겠습니다.

​

> 스토캐스틱(Stochastic Slow)
> 
> 활용 방법

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfNzAg/MDAxNTk2NTQxNzk2NDM2.UtGg8Vu60HTstIf2Dl-VxRTnC65WTyig6y1Sg6HUlUkg.9a3Mv2SSXdZnLwGVwI75Gzq8KTO4oi_yk3xry9qVrrog.PNG.rmsgud2007/%EB%B3%B4%EB%8A%94%EB%B2%95.png?type=w80_blur)

**스토캐스틱 지표를 보는 방법은**

**크게 두 가지로 나뉩니다.**

​

보라색 동그라미로 색칠된 ​**과매수**

**구간과 과매도 구간을 활용한 방법**과

회색 동그라미로 표시된 **%K, %D 선을**

**활용한 방법**이 있습니다.

​

참고로 갈색선이 %K, 초록색 선이 %D,

과매수 구간이 빨간색, 과매도 구간이

파란색인데 이는 원하시는 색깔로

마음껏 바꾸셔도 상관없고 본인이 이것저것

만져보신 후 최적의 값을 찾아내 매매에

임하셔도 됩니다.

​

**비밀인데**

**저는 계산 값을 10, 5, 3으로 일봉이 아닌**

**주봉을 보는데 사용합니다 깔깔!**

> 과매수, 과매도 구간 활용

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMTk3/MDAxNTk2NTQyMDU5MDM5.g4RIVdn14LdL-beGP093EmIKjaMBj13DjRv7f5G8vBsg.7uo9CiNi_XhiFD_QTtBigvUVV9ZL8mCtbOZJxmszjMUg.PNG.rmsgud2007/%ED%99%9C%EC%9A%A9.png?type=w80_blur)

일반적으로 스토캐스틱 수치가 **80% 이상**일

경우에는 많은 투자자들이 매수하여 주가가

오른 상황이기 때문에 **'과매수 구간'**이라

부르고 반대로 **20% 미만**일 경우에는

**'과매도 구간'**이라고 부릅니다.

​

갈색깔의 %K 선이 과매도 구간에서

뚫고 나가는 **골든크로스 시점이**

**매수 시점**입니다.

​

처음이신 분들은 무슨 말인지

헷갈릴 수도 있으니 차트를 보면서

설명드리겠습니다!

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfOTcg/MDAxNTk2NTQyNDY5MTk1.3Le_z2NE4G2lKMdMmTykRwE4KXkHhj0J4wn6s54CUbMg.vmmrqDWMgO50RUqjsciI4UcVOqpi-6wAxGoBev74qo0g.PNG.rmsgud2007/%EC%83%81%EC%8A%B9.png?type=w80_blur)

갈색의 **%K 선이 과매도 구간을**

**뚫고 나간 이후 주가가 상향**하는 것이

보이시나요?

​

물론 반대로 과매수 구간에서

뚫고 내려가는 시점이 매도 시점이라

부르는데 동일한 차트를 보면서

설명드리겠습니다.

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjE5/MDAxNTk2NTQyNjk4MDgx.XyyK9sEUHa3JAShpl3vKt8_5xEaFUvLQzv7SjA2vzbIg.5VedkLQPxuRH_06elV8gayv1bIhAqop1pF6Doolb420g.PNG.rmsgud2007/%ED%95%98%EB%9D%BD.png?type=w800)

**%K 선이 과매수 구간에서**

**빠져나와 내려가는 동시에 주가가**

**하락**하는 모습을 볼 수 있는데

빠져나오는 시점이 바로 **매도 시점**입니다.

​

> %K 선과 %D 선을
> 
> 활용한 매매 방법

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMyAg/MDAxNTk2NTQyOTEwMzE1.cFMM0FezNgdXrtyXRprSZMeXineEXcIDM3lI0tPzq8cg.3DoO3LXQRC0XYPAVmUT2-YebfP6gxYKdbfAgR7iQIjYg.PNG.rmsgud2007/%EC%83%89.png?type=w800)

앞서 말씀드렸듯이

갈색선이 %K, 녹색선이 %D인데

%K 선이 %D 선을 뚫고 올라가는

**골든크로스 시점이 매수 타이밍이고**

**뚫고 내려가는 시점이 매도 타이밍입니다.**

​

말로만 설명하면 어려우니 이번에도

차트를 보면서 설명드릴게요.

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMTc4/MDAxNTk2NTQzMjk2NjQ0.IDekYRbd8bCxHzbjxyISrGotaNRb7ijv-Y4fya44_DMg.Rs52-TI1yQc0MVduJtuwF8sFKhjLnf_6a2jJJwF4Ebwg.PNG.rmsgud2007/%EC%98%A4%EB%A6%84.png?type=w800)

동그라미로 표시한 부분이 **%K 선이**

**%D 선을 뚫고 올라가는 골든크로스**

**시점**이며 이 시점부터 주가는 오르는 것을

확인할 수 있습니다.

​

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjU5/MDAxNTk2NTQzMzMyMDM3.QbhoMpvFnJqdYiXnxeRUOGLDRgx75XOkyr3AvM1_NIUg.QV3CoU2nKp1ECw0Z1aMiU3wuJ-1P2LgLspm4xVUNuCsg.PNG.rmsgud2007/%EB%82%B4%EB%A6%BC.png?type=w800)

반대로 **%K 선이 %D 선을 뚫고 내려가는**

**데드크로스 시점**과 함께 주가는

떨어지는 모습을 볼 수 있는데 이 시점이

매도 타이밍이라고 보시면 됩니다.

​

과매수 구간, 과매도 구간을 활용한

방법과 %K선, %D 선을 활용한 방법을

제외하고도 잘 사용하지 않는 방법이지만

기준선을 활용한 매매 방법도 있습니다.

​

포스팅하려던 계획에는 없었지만

이왕 포스팅하는 김에 기본적인

개념 정도만 알려드리겠습니다!

> 기준선을 활용한
> 
> 매매 방법

![](https://mblogthumb-phinf.pstatic.net/MjAyMDA4MDRfMjkg/MDAxNTk2NTQzNTg3ODEx.UjEjz9PutbyH0AFQr2LjEN41tAj7N42N9cZ5qNn3IEEg.8XJHRIf-TL76kzwomY-COLrh1fqazJma5DG9LWNTrqMg.PNG.rmsgud2007/%EA%B8%B0%EC%A4%80%EC%84%A0.png?type=w800)

우측에 보시면 0%부터 100%까지

있는 게 보이시나요?

​

일반적으로는 **50% 선을 기준**으로 하고

%K 선과 %D 선이 기준선 아래에서

**상향 돌파하는 시점이** **매수 시점****,**

**하향 돌파하는 시점이** **매도 시점****입니다.**

---

%K, %D, 기준선에 사용되는 값은

임의대로 설정하셔도 좋습니다만

보조 지표는 보조 지표일 뿐 이것만 믿고

투자하시면 큰일 납니다..!

​

투자는 항상 신중하게!

​

오늘도 유익한 포스팅이었으면

좋겠습니다.