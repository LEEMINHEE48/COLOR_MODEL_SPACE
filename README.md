Various Colorspaces(Models) 
===========================

YUV
---
YUV 

RGB can express aubandant and detail color, But it has very big volume. 
----> If you use YUV......


      |white|Grey|Black|
     |------|-----|-----|
RGB  |255,255,255|128,128,128|0,0,0|
YUV  |235,0,0|128,0,0|16,0,0|
 
 
 |   White        |     Grey          | Black 
---   ----------         --------------   ----------
RGB | 255,255,255    |   128,128,128     |  0,0,0
---   ------------       ------------      -------
YUV | 235,0,0        |   128,0,0         | 16,0,0

It can conpress from big volume to more(1/2) small volume 

<img width="250" alt="스크린샷 2020-09-27 오전 12 14 59" src="https://user-images.githubusercontent.com/70868719/94343917-83999500-0056-11eb-9472-39fd71fac77e.png">


ACES Colorspace
---------------
The Academy Color Encoding System  (ACES) is a color image encoding system created by hundreds of industry professionals under the auspices of the  Academy of Motion Picture Arts and Sciences. ACES allows for a fully encompassing color accurate workflow, with "seamless interchange of high quality motion picture images regardless of source".

- 차세대 색관리 시스템으로서 디지털 영상 마스터링을 원활히 수행하기 위한 2004년도에 개발이 시작되어 현재 미국 영화텔레비저닉술인협회(SMPTE)의 차세대 색관리 표준(TC – 10 E, TC -31fs). 
1993년도에 개발되어 최근까지도 범용적으로 사용되어왔던 DPX포맷은 20년의 세월을 거치며 이미 기능이 상실된 필름 기반 10bit 포맷
비경제적이고 비효율적이며 무엇보다도 화질열화를 유발하는 DPX 포맷은 초과화질 UHD에서는 사용이 힘듬 

**But, SONY F65, F55, Blackmagic Cinema Camera, Arri Alexa, RED Dragon 등의 디지털 소스들은 곧바로 ACES 색곤간으로 변환이 된다.  특히 ACES 색공간은 인간의 가시영역을 나타내는 CLE XYZ 1931 색공간을 모두 포함하고 있다. 디지털 시네마 환경에서 사용되는 DCI-P3 색공간, HDTV Rec.709 및 UHDTV Rec.202 색공간을 모두 포함**



ACES는 제작현장에서의 시네마룩과 후반작업에서의 색보정 불확실성제거(International Standard Transformation) , 넓은 색공간과 색심도(High Dinamic Range + Wide Gamut)를 보유함으로서 제작과정에서의 풍부한 색감과 계조를 유지할 수 있는 것 뿐만아니라 화면지향 선형화 기술을 사용함으로서 후반작업에서 보다 자유로운 창작환경을 제공할 수 있다.


밝기에 대해서 사람의 안구는 비선형의 특성을 갖고 있다. 즉, 밝은 부분에 대하여 반응하는 정도가 어두운 부분에 반응하는 정도와 다르다는 것이다. 그래서 Gamma Correction 기술을 사용한다. 
화면을 밝게 한다는 것은 R,G,B 각 원색에 대하여 확장범위가 서로 달라진다는 것이다. 

**쉽게 말해서, 밝은 화면을 확보하기 위해 더 많은 Green Gamut 특성을 필요로 하게 되는 것 이다.**  


<img width="1225" alt="스크린샷 2020-09-26 오후 8 36 47" src="https://user-images.githubusercontent.com/70868719/94343603-2270c200-0054-11eb-9df4-b1b331ce12f1.png">


<img width="842" alt="스크린샷 2020-09-26 오후 8 36 54" src="https://user-images.githubusercontent.com/70868719/94343618-416f5400-0054-11eb-80b7-bc07959effb0.png">


<img width="1057" alt="스크린샷 2020-09-26 오후 8 41 29" src="https://user-images.githubusercontent.com/70868719/94343625-53e98d80-0054-11eb-9c01-2e0c483d5fec.png">

<img width="1135" alt="스크린샷 2020-09-26 오후 8 46 07" src="https://user-images.githubusercontent.com/70868719/94343656-8eebc100-0054-11eb-9c2b-057f09db21cd.png">


LUT ( Lookup Table )
====================
순람표 또는 룩업 테이블은 컴퓨터 과학에서 일반적으로 배열이나 연관 배열로 된 데이터 구조로, 런타임 계산을 더 단순한 배열 색인화 과정으로 대체하는 데 자주. 쓰인다. 처리 시간의 적약은 중요할 수 있는데, 이는 메모리로부터 값을 받아오는 것이 더 일이 많이 드는 계산이나 입출력 기능을 거치는 것보다 더 빠르기 때문이다. 
………..**At Color work…. ‘영상값을 표시값으로 사용하기 위해 수치 영상 처리에서 사용되는 테이블’.**

**Log --> more fastly convert to Rec.709  색보정작업을 진행할때 일종의 공식을 만들어 이 공식을 이용하여 손쉽게 Rec.709 등의 표준 색영역으로 색교정을 할수있게함** 

종류는 크게 1D(dimention) LUT, 3D LUT가 있는데, 

#1 **1D LUT**는 커브 곡선이나 커브를 움직이는 보정값(Lift, Gamma, Gain, Contrast 등과 1:1로 매치된다. But, Hue,Saturation을 보정해 보면 1D LUT에는 아무런 변화가 없다 그래서 1D LUT는 “휘도 곡선”을 보정할때 사용한다고들 한다.

<img width="667" alt="스크린샷 2020-09-27 오전 12 02 42" src="https://user-images.githubusercontent.com/70868719/94343692-cfe3d580-0054-11eb-8cb0-d75b8d477bf1.png">


**But, 1D역시 RGB 3개의 채널별로 LUT를 만든다. ----- Lift, Gamma, Curve는 모두 RGB 채널별로 값을 보정할 수가 있고, 이 보정된 값은 1D LUT에 그대로 적용된다.**

#2 **3D** 에서는 1D에서 표현하지 못하는 Hue와 Saturation 보정 값까지 담을 수 있다. _(XYZ축의 공간 좌표로 표현하기 때문이다.)_


<img width="689" alt="스크린샷 2020-09-26 오후 9 33 46" src="https://user-images.githubusercontent.com/70868719/94343697-e12ce200-0054-11eb-9a7e-f02f0e5da9eb.png">


1D LUT 에서는 입력값과 출력값이 1:1로 매치되지만, 3D 에서 이렇게 해버리면 엄청난 좌표값들이 필요하기 때문에 실제로는 그렇게 하지 않고, 일부 값만 표시하고 나머지 부분은 ‘보간’처리 한다.  Ex) 10 bit에서는 종종 17X17X17개의 공간 좌표로 표헌한다고 한다.(SIZE 조절가능)  


LUT에서 표현할 수 없는 것은 ‘세컨드리’,’마스크’,’그라데이션’… 오로지 프라이머리만 가능하며, 한번 만들어진 LUT 수정 불가능  LOOK PRESET와 다른점 
소니, 캐논, 블랙매직디자인, 아리, 레드 등의 회사는 각 회사의 로그( S-log, C-log등)을 제공하며 다빈치 리졸브 등의 색보정 프로그램 혹은 카메라 회사에서 자체적으로 Rec.709등의 표준 색상으로 손쉽게 바꿀수있는 LUT 등을 제공하고있음.




Log Gamma란? 
============

**Log의 주요 목적은 다이내믹 레인지를 확장하는것**

가장 좋은 방법은 Raw 파일을 사용하여 레코딩 하는 것이지만, Raw 파일의 용량과 처리 속도등의 문제로 시네마를 위한 하이앤드 카메라가 아닌 이상 사용하기 어려움. 

그래서 하이앤드 카메라가 아닌 소형카메라에서는 H.264 등의 압축포맷을 이용하여 레코딩. 



**압축 포맷이다 보니 Raw 포맷보다 손실되는 데이터가 많음 ----->화질, 다이내믹 레인지 등이 손실됨**


Log는 이런 동영상에서의 단점, 그 중에서도 좁아지는 다이나믹 레인지를 좀 더 넓혀서 명도 표현의 단계를 확장하기 위해 고안된방법 --->밝기를 나타내는 감마곡선을 대수(Log) 함수를 이용해서 더 넓은 명도 표현이 가능하도록한다. 실질적인 용량/비트율 상승없이 명도 단계만 늘렸으므로 콘트라스트와 채도가 감소한 일명 Flat 이미지로 보인다.


더 넓은 다이나믹레인지를 위해 어두운 부분의 색정보를 일정 희생시키는 방식이고 감소된 대비와 채도를 보정하기 위한 후반 색보정 촬영이 필요함.


<img width="1300" alt="스크린샷 2020-09-26 오후 10 30 49" src="https://user-images.githubusercontent.com/70868719/94343714-07eb1880-0055-11eb-911a-f21aa9085334.png">


다이내믹 레인지만 확장된 형태이므로 청명한 자연 풍광 등 밝기/명도 차가 큰 환경에서 효과적이지만, 그 대신 기본 최저감도(ISO)상승이 불가피 하므로 ND 필터 등을 사용해야 하는 경우가 많아지고 감도 증가로 노이즈 증가도 신경 써야 한다. 
 

SRGB VS LOG 


리니어 컬러커브(SRGB) 보다 LOG 컬러 커브가 이미ㅣㅈ으 더 어두운 부분이 Shdow를 보유하기 위해 위 치솟아 있고, 커브의 꼭대기는 Highlight을 보유하기 위해 아래쪽으로 꺽여있다.  

<img width="841" alt="스크린샷 2020-09-27 오전 12 21 34" src="https://user-images.githubusercontent.com/70868719/94344106-f9523080-0057-11eb-84d3-160a66f0fb53.png">


------> 더 많은 다이나믹 레인지 확장 가능 









참고자료
-------
https://surplusperson.tistory.com/457 
http://schoolofcolor.org/post-hdtv-part-2/
https://blog.naver.com/laizenti/221722862804
http://keruluke.com/archived_web/kft/vol4/lookuptable/
https://m.blog.naver.com/PostView.nhn?blogId=pixitmedia&logNo=220975895397&proxyReferer=https:%2F%2Fwww.google.co.kr%2F

