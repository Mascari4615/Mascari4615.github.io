---
title: "색"
# description: ""
categories: [컴퓨터, 그래픽]
tags: []
image: "/assets/img/background/kururu-lab.jpg"

date: 2024-11-13. 06:37 # Init
last_modified_at: 2025-06-10. 23:06 # 네이밍: RGB -> Color, +HDR:, +메모: 관련 링크
---

## 머리말

---

Gizmos의 X, Y, Z 축은 왜 빨간색, 초록색, 파란색일까?  

## 색과 빛

---

### 감산 혼합

잉크.  
색의 삼원색: CMYK로 이루어진 색을 더하면 더할수록 어두워지며, 모두 더하면 검은색이 되는 색의 체계.  

### 가산 혼합

빛.  
빛의 삼원색: RGB로 이루어진 색을 더하면 더할수록 밝아지며, 모두 더하면 흰색이 되는 색의 체계.  

## 모니터의 색과 빛

---

모니터는 빛으로 색을 표현하고, 때문에 가산 혼합을 사용합니다.  

### How

일반적으로 컬러 모니터는 RGB로 구성된 3개의 '서브 픽셀 (Subpixel)' 로 이루어져 있습니다.  
모니터의 한 픽셀을 이루는 기본구조는 마치 R, G, B (Red, Green, Blue)의 색으로 빛나는 3개의 조명이 붙어있는 모습이라고 생각할 수 있습니다.  
즉, 3개의 조명이 모두 동시에 빛난다고 가정했을 때, 이 3개의 색을 멀리서 보면 하나로 합쳐져서 흰색처럼 보이게 되는 것입니다.  

## 색은 숫자다

---

### 모니터에 나타내는 색을 숫자로 표현하기

빨간색은 3개의 조명 중 R 조명만 켜지게 되고, 정확하진 않겠지만, 밝기로만 따져보면 흰색보다 약 1/3 쯤으로 어두워졌을 것이라고 예상할 수 있겠습니다.

### 컬러를 숫자로 나타내보기

한 픽셀의 색을 결정하는 코드를 '픽셀 셰이더(Pixel Shader)' 라고 부릅니다

### 컬러를 숫자로 인식해 보기

RGB는 합쳐 놓으면 컬러로 보이지만 따로따로 놓으면 흑백으로 표현된다는 것입니다.
예를 들어 R 값만 있고 나머지는 없다고 하면, R 값의 숫자는 더 이상 컬러를 나타내는 것이 아니라 R 값의 '강도'만 표현하는 한 자리 숫자일 뿐입니다.
마치 '붉은색 전구를 켜는데 필요한 전기의 힘' 같은 느낌처럼 말입니다.
그 힘 자체가 붉은색을 나타내지는 않으므로 각 컬러의 채널을 따로 볼 때는 흑백으로 '강도'만 표현됩니다.
그리고 그것은 알파 채널도 마찬가지입니다.
투명도도 따로 떼어 놓고 보면 흑백의 '강도'일 뿐입니다.

## 색 연산

---

### 컬러를 연산해 보기

노란색 (1,1,0) + 빨간색 (1,0,0) 는 어떻게 될까요?
일단 숫자로는 (2,1,0) 이 됩니다.
정답은 노란색입니다.
비록 숫자는 1을 넘어섰지만 이것은 숫자로 존재만 할 뿐, 모니터에서는 1이상의 색상은 표현할 수 없게 됩니다.
ㄴ [여기에서 우리는 '1보다 밝은색' 즉, '흰색보다 밝은색' 이 실제로 존재한다는 것을 알 수 있습니다. 실제 세계에서도 '눈부실 정도로 밝은 빛' 이 존재하듯이 말입니다. 하지만 모니터로 그 색을 출력해내는 것이 불가는하기 때문에, 눈으로는 1이 넘어가는 밝은색을 구별해낼 수 없다는 것에 주의해야 합니다. 나중에 색상을 추가로 연산할 때 오차가 일어날 수 있기 때문입니다. + {이 부분은 HDR 등에 연관되며, 블룸 (Bloom) 효과 등을 만들 때 유용하게 사용됩니다.}]
마찬가지로 뺄셈도 계산에 따라서는 0 이하의 색상이 만들어질 수 있습니다.
하지만 0 이하의 숫자는 0으로 보이기 때문에 빨간색에서 파란색을 뺀 색은 그냥 빨간색처럼 보이게 됩니다.
물론 숫자로는 -1이 그대로 유지되고 있다는 것으 주의하세여
★ 나눗셈은 상대적으로 곱셈보다 느리다

### 컬러의 반전 (Invert)

1 = float1 (1) = float3 (1, 1, 1) = float4 (1,1,1,1)
이 때 1자리 숫자의 경우 굳이 앞에 float을 붙이지 않음, 그냥 1이라고 씀
1에서 어떤 색을 빼면 그 색이 반전됩니다.
1-x 계산은 흰색을 검정색으로, 검정색을 흰색으로 뒤집어 주는 등의 역할을 할 수 있기 때문에 실제 셰이더 계산에서 자주 사용되곤 합니다.

### Swizzling

= mix up, 휘몰아치는  
벡터의 구성 요소를 임의로 재정렬하고 결합하여 벡터를 구성하는 기능 (CG에서)  

- `Pointer Swizzling`
  - 포인터로 링크된 자료 구조 단위를, ID나 이름 등으로 대체함으로써 프로그램을 다시 시작하더라도 성공적으로 파일 데이터를 로드, 역직렬화 시키는 방법

- 참고로 마인크래프트의 `휘몰아치는 칼날`은 `Sweeping`이다.  

## HDR

---

High Dynamic Range  
1보다 밝은 색, 0보다 어두운 색이 존재하고 계산되는 상태  

유니티:  
\[ColorUsage(true,true)\] 어트리뷰트로 color 변수 컬러피커 HDR 가능  

## 메모

---

- <https://colorpalettes.net/>
- <https://coolors.co/ef476f-ffd166-06d6a0-118ab2-073b4c>
- <https://mycolor.space/?hex=%23845EC2&sub=1#AB372E&sub=1>
- [ColorBlind ColorFilter](https://www.toptal.com/designers/colorfilter)
- [Adobe Color](https://color.adobe.com/ko/create/color-wheel)
- [컬러 팔레뜨](https://lospec.com/palette-list)

### 참고

- [참고: 색상 표현 기본원리, 색 연산 기초](https://rusalgames.tistory.com/17)
