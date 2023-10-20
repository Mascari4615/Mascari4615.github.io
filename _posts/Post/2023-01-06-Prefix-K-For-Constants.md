---
title: "🌒 상수 이름에 접두사 k, 헝가리안 표기법"
date: 2023-01-06. 23:46
categories: ⭐Computer 🌒Programming
---

### 💎 상수 이름에 접두사 k

---

[참고](https://stackoverflow.com/questions/5016622/where-does-the-k-prefix-for-constants-come-from)

> 요약 :  
> c는 char의 약자로 이미 쓰고 있기 때문에,  
> 수학에서 상수로 쓰이고, 독일어로 상수의 첫 글자인 (konstant), k 를 쓰게 되었다.  
> ... 혹은 그저 정말 발음이 유사해서 썼다던지.  

---

```cs
private const int kVariable = 1;
```

위처럼 상수 이름 앞에 k를 붙이는 경우가 있다.  

과거에 약한 타입 언어(Weak Type Language)가 쓰일 때,  
지금 같이 자동 타입 검사가 있지 않았던 탓에, 타입을 잘못 오해하고 사용하는 경우가 빈번했다.  

이 문제를 해결하기 위해 헝가리안이었던 마이크로소프트의 찰스 시모니가 제안한 방법이,  
바로 헝가리안 표기법이다.  

```cs
private bool bVariable = true;
private char cVariable = 'A';
```

헝가리안 표기법은 위와 같이 변수 이름 앞에 변수 타입을 명시하는 표기법이다.  
이렇게 변수 이름 앞에 변수 타입을 지정함으로써, 변수를 쓰면서 그 변수 타입이 무엇인지 바로 알 수 있었다.  
이를 통해 변수 타입을 잘못 오해하고 사용하는 문제를 해결하고자 했다.  

이후 시간이 흘러, 강한 타입 언어(String Type Language)가 등장하면서 주요 언어로 더욱 쓰이게 되었는데,  
강한 타입 언어는 타입을 분명하게 알 수 있었음에도 불구하고, 많은 팀과 프로그래머들이 헝가리안 표기법을 그대로 채택했다고 한다.  

내 생각에는 참고 링크의 답변의 의견처럼,  
사용된 맥락을 생각하지 않고 무분별하게 이전 관습을 차용함으로서 생긴 오용이라고 생각된다.  

물론 내가 프로그래밍을 시작한 시점엔 이미 IDE가 자동 타입 검사를 해주는 편리함이 있었기에,  
당시 상황에 대해 뭐라 할 자격은 없다고 생각이 들기는 하지만..

무튼 헝가리안 표기법의 목적은 변수 타입을 한눈에 볼 수 있음에 있는데,  
지금은 단순히 변수에 마우스만 올려도 타입을 알려주는 편리한 IDE가 존재하기에,  
굳이 가독성을 떨궈가며 헝가리안 표기법을 사용할 이유는 없는 것 같다.  

첫 글자가 똑같은 타입에 대해서, 계속해서 상수와 같은 특수한 케이스를 만들수도도 없고 말이다.  