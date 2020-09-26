# COLOR_MODEL_SPACE

Various Colorspaces(Models) 
===========================

YUV
---
YUV 

RGB can express aubandant and detail color, But it has very big volume. 
----> If you use YUV......


    
    
    |   White        |     Grey          | Black 
---   ----------         --------------   ----------
RGB | 255,255,255    |   128,128,128     |  0,0,0
---   ------------       ------------      -------
YUV | 235,0,0        |   128,0,0         | 16,0,0

It can conpress from big volume to more(1/2) small volume 




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


LUT ( Lookup Table )
====================
순람표 또는 룩업 테이블은 컴퓨터 과학에서 일반적으로 배열이나 연관 배열로 된 데이터 구조로, 런타임 계산을 더 단순한 배열 색인화 과정으로 대체하는 데 자주. 쓰인다. 처리 시간의 적약은 중요할 수 있는데, 이는 메모리로부터 값을 받아오는 것이 더 일이 많이 드는 계산이나 입출력 기능을 거치는 것보다 더 빠르기 때문이다. 
………..**At Color work…. ‘영상값을 표시값으로 사용하기 위해 수치 영상 처리에서 사용되는 테이블’.**

**Log --> more fastly convert to Rec.709  색보정작업을 진행할때 일종의 공식을 만들어 이 공식을 이용하여 손쉽게 Rec.709 등의 표준 색영역으로 색교정을 할수있게함** 

종류는 크게 1D(dimention) LUT, 3D LUT가 있는데, 

#1 **1D LUT**는 커브 곡선이나 커브를 움직이는 보정값(Lift, Gamma, Gain, Contrast 등과 1:1로 매치된다. But, Hue,Saturation을 보정해 보면 1D LUT에는 아무런 변화가 없다 그래서 1D LUT는 “휘도 곡선”을 보정할때 사용한다고들 한다.

<u>But, 1D역시 RGB 3개의 채널별로 LUT를 만든다. ----- Lift, Gamma, Curve는 모두 RGB 채널별로 값을 보정할 수가 있고, 이 보정된 값은 1D LUT에 그대로 적용된다.</u> 
