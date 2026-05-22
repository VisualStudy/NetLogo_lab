# NetLogo_lab
NetLogo를 연구합니다.

# 프랙탈과 코흐 곡선 이해하기

## 1. 프랙탈이란?

프랙탈(fractal)이란 작은 구조가 전체 구조와 비슷한 형태를 반복하는 기하학적 구조를 말한다.

쉽게 말하면, 어떤 도형을 자세히 들여다보았을 때 작은 부분도 전체와 비슷한 모양을 가지고 있다면 그것을 프랙탈이라고 한다.

예를 들어 나뭇가지, 번개, 해안선, 눈송이, 혈관, 브로콜리 같은 자연물에서는 프랙탈과 비슷한 구조를 볼 수 있다.

---

## 2. 프랙탈의 핵심 특징

프랙탈의 가장 중요한 특징은 다음과 같다.

## 2.1 자기유사성

자기유사성이란 부분의 모양이 전체의 모양과 비슷하게 반복되는 성질이다.

예를 들어 나뭇가지를 보면 큰 줄기에서 작은 가지가 뻗고, 그 작은 가지에서 더 작은 가지가 다시 뻗는다.  
이처럼 작은 구조가 전체 구조와 비슷하게 반복되는 것을 자기유사성이라고 한다.

```text
전체 모양
 └─ 작은 부분
     └─ 더 작은 부분
         └─ 더 작은 부분
```

프랙탈은 이러한 자기유사성을 가진 대표적인 구조이다.

---

## 2.2 반복

프랙탈은 같은 규칙을 반복해서 적용하면서 만들어진다.

처음에는 단순한 선이나 도형에서 시작하지만, 같은 규칙을 여러 번 적용하면 점점 복잡한 구조가 만들어진다.

예를 들어 하나의 선을 일정한 규칙으로 꺾고, 그 꺾인 선에 다시 같은 규칙을 적용하면 프랙탈 구조가 된다.

```text
1단계: 단순한 선
2단계: 선을 나누고 꺾음
3단계: 나누어진 선마다 다시 같은 규칙 적용
4단계: 더 복잡한 구조 생성
```

---

## 2.3 단순한 규칙에서 복잡한 형태가 만들어짐

프랙탈은 복잡해 보이지만, 실제로는 매우 단순한 규칙에서 시작되는 경우가 많다.

코흐 곡선도 마찬가지이다.  
기본 규칙은 단순하다.

```text
1. 선을 3등분한다.
2. 가운데 부분을 삼각형처럼 꺾는다.
3. 새로 생긴 각 선분에 같은 과정을 반복한다.
```

이 단순한 규칙을 반복하면 복잡한 눈송이 같은 모양이 만들어진다.

---

## 3. 프랙탈의 예시

프랙탈은 수학적 도형뿐 아니라 자연 현상에서도 자주 나타난다.

| 예시 | 설명 |
|---|---|
| 나뭇가지 | 큰 가지에서 작은 가지가 반복적으로 뻗음 |
| 번개 | 갈라지는 모양이 여러 단계로 반복됨 |
| 해안선 | 멀리서 본 굴곡과 가까이서 본 굴곡이 비슷함 |
| 눈송이 | 결정 구조가 반복적으로 나타남 |
| 혈관 | 큰 혈관에서 작은 혈관으로 계속 갈라짐 |
| 브로콜리 | 전체 모양과 작은 봉오리의 모양이 비슷함 |

이처럼 프랙탈은 자연 속 복잡한 구조를 설명하는 데 자주 사용된다.

---

## 4. 코흐 곡선이란?

코흐 곡선(Koch curve)은 대표적인 프랙탈 도형 중 하나이다.

1904년 스웨덴 수학자 헬게 폰 코흐(Helge von Koch)가 소개한 도형으로, 하나의 선분을 일정한 규칙에 따라 계속 변형하여 만든다.

코흐 곡선은 단순한 선에서 시작하지만, 같은 변형 규칙을 반복하면 점점 복잡한 꺾인 선이 된다.

---

## 5. 코흐 곡선이 만들어지는 원리

코흐 곡선은 다음과 같은 규칙으로 만들어진다.

## 5.1 시작 단계

처음에는 하나의 직선으로 시작한다.

```text
────────────
```

---

## 5.2 1단계 변형

직선을 3등분한다.

```text
──── ──── ────
```

가운데 부분을 바깥쪽으로 꺾어 정삼각형의 두 변처럼 만든다.

```text
    /\
___/  \___
```

즉, 원래 직선 하나가 네 개의 작은 선분으로 바뀐다.

```text
원래 선분 1개
→ 작은 선분 4개
```

---

## 5.3 2단계 변형

1단계에서 생긴 네 개의 작은 선분 각각에 다시 같은 규칙을 적용한다.

```text
각 선분을 다시 3등분
→ 가운데 부분을 꺾음
→ 더 많은 작은 선분 생성
```

---

## 5.4 반복

이 과정을 계속 반복하면 점점 더 복잡한 곡선이 만들어진다.

```text
0단계: 직선 1개
1단계: 작은 선분 4개
2단계: 작은 선분 16개
3단계: 작은 선분 64개
4단계: 작은 선분 256개
```

즉, 단계가 한 번 증가할 때마다 선분의 개수는 4배씩 증가한다.

---

## 6. 코흐 눈송이란?

코흐 눈송이(Koch snowflake)는 코흐 곡선을 이용해 만든 닫힌 프랙탈 도형이다.

보통 정삼각형의 세 변에 각각 코흐 곡선 규칙을 반복해서 적용하면 코흐 눈송이가 된다.

```text
정삼각형
→ 각 변을 코흐 곡선으로 변형
→ 눈송이와 비슷한 프랙탈 도형 생성
```

코흐 눈송이는 바깥 경계가 계속 복잡해지지만, 전체적으로는 눈꽃처럼 아름다운 대칭 구조를 가진다.

---

## 7. 코흐 곡선의 특징

## 7.1 자기유사성을 가진다

코흐 곡선은 작은 부분을 확대해도 전체와 비슷한 꺾인 구조가 반복된다.

이 때문에 코흐 곡선은 대표적인 자기유사 프랙탈이다.

---

## 7.2 단계가 증가할수록 선분의 수가 많아진다

코흐 곡선은 한 단계마다 각 선분이 4개의 선분으로 바뀐다.

따라서 선분의 개수는 다음과 같이 증가한다.

| 단계 | 선분 개수 |
|---:|---:|
| 0단계 | 1개 |
| 1단계 | 4개 |
| 2단계 | 16개 |
| 3단계 | 64개 |
| 4단계 | 256개 |

일반적으로 `n`단계의 선분 개수는 다음과 같다.

```text
4^n
```

---

## 7.3 각 선분의 길이는 짧아진다

코흐 곡선에서는 한 단계가 진행될 때마다 선분의 길이가 1/3로 줄어든다.

예를 들어 처음 선분 길이가 `side`라면 다음과 같이 된다.

```text
0단계: side
1단계: side / 3
2단계: side / 9
3단계: side / 27
```

즉, 단계가 깊어질수록 선 하나의 길이는 짧아지지만, 선분의 개수는 훨씬 많아진다.

---

## 7.4 전체 길이는 계속 증가한다

코흐 곡선에서는 한 선분이 4개의 선분으로 바뀌고, 각각의 길이는 원래 길이의 1/3이 된다.

따라서 한 단계가 진행되면 전체 길이는 다음과 같이 변한다.

```text
기존 길이 × 4/3
```

즉, 단계가 증가할수록 전체 경계 길이는 계속 길어진다.

```text
0단계: L
1단계: L × 4/3
2단계: L × (4/3)^2
3단계: L × (4/3)^3
```

이론적으로 무한히 반복하면 코흐 곡선의 길이는 무한히 길어진다.

---

## 8. NetLogo 코드와 코흐 곡선의 관계

NetLogo 코드에서 코흐 곡선의 핵심은 다음 부분이다.

```netlogo
to snowflake [n side]
  if n = 0 [fd side stop]

  snowflake (n - 1) (side / 3) 
  lt 60

  snowflake (n - 1) (side / 3) 
  rt 120

  snowflake (n - 1) (side / 3) 
  lt 60

  snowflake (n - 1) (side / 3) 
end
```

이 코드는 하나의 선을 네 개의 작은 선으로 바꾸는 역할을 한다.

---

## 8.1 종료 조건

```netlogo
if n = 0 [fd side stop]
```

`n`이 0이면 더 이상 나누지 않고 앞으로 `side`만큼 이동한다.

이때 실제 선이 그려진다.

---

## 8.2 선분을 3등분하는 구조

```netlogo
snowflake (n - 1) (side / 3)
```

이 부분은 현재 선분을 더 작은 선분으로 나누는 역할을 한다.

코흐 곡선에서는 선분을 3등분하므로 `side / 3`을 사용한다.

---

## 8.3 코흐 곡선의 꺾임

```netlogo
lt 60
rt 120
lt 60
```

이 회전 구조는 선을 정삼각형 모양으로 꺾기 위해 사용된다.

| 코드 | 의미 |
|---|---|
| `lt 60` | 왼쪽으로 60도 회전 |
| `rt 120` | 오른쪽으로 120도 회전 |
| `lt 60` | 왼쪽으로 60도 회전 |

이 구조 때문에 단순한 직선이 산 모양으로 변하고, 이 과정이 반복되면서 코흐 곡선이 만들어진다.

---

## 9. 코흐 곡선과 코흐 눈송이의 차이

| 구분 | 코흐 곡선 | 코흐 눈송이 |
|---|---|---|
| 시작 도형 | 하나의 선분 | 정삼각형 |
| 구조 | 열린 곡선 | 닫힌 도형 |
| 생성 방식 | 한 선분에 규칙 반복 | 삼각형의 세 변에 규칙 반복 |
| 결과 | 꺾인 프랙탈 선 | 눈송이 같은 프랙탈 도형 |

즉, 코흐 곡선은 하나의 프랙탈 선이고, 코흐 눈송이는 그 곡선을 여러 변에 적용해 만든 닫힌 도형이다.

---

## 10. 요약

프랙탈은 작은 부분이 전체와 비슷한 구조를 반복하는 도형이다.  
코흐 곡선은 대표적인 프랙탈 도형으로, 하나의 선분을 3등분하고 가운데 부분을 삼각형처럼 꺾는 규칙을 반복하여 만든다.

코흐 곡선의 핵심 특징은 다음과 같다.

```text
1. 자기유사성을 가진다.
2. 같은 규칙을 반복하여 만든다.
3. 한 단계마다 선분 수가 4배로 증가한다.
4. 각 선분의 길이는 1/3로 줄어든다.
5. 전체 길이는 단계가 깊어질수록 증가한다.
```

코흐 눈송이는 정삼각형의 세 변에 코흐 곡선 규칙을 적용한 프랙탈 도형이다.  
NetLogo에서는 `turtle`의 이동과 회전, 그리고 재귀 호출을 이용해 이러한 프랙탈 구조를 구현할 수 있다.

# NetLogo Fractal Drawing Model Documentation

## 1. 개요

이 NetLogo 모델은 `turtle`을 이용하여 선을 그리고, 반복과 재귀를 통해 프랙탈 구조를 생성하는 예제이다.

기본적으로 거북이 한 마리를 생성한 뒤, `fd`, `lt`, `rt`, `hatch` 명령을 사용하여 선을 분기시키거나, 재귀 프로시저 `snowflake`를 통해 코흐 눈송이와 유사한 프랙탈 패턴을 그린다.

이 모델은 두 가지 방식으로 프랙탈 구조를 만들 수 있다.

```text
1. iterate를 이용한 hatch 방식
2. snowflake를 이용한 recursive 방식
```

---

## 2. 전체 코드

```netlogo
to setup
  clear-all
  create-turtles 1
  [
    set heading 90
    set color blue
    pd
  ]
  reset-ticks
end

to step
  ask turtles [ iterate ]
  tick
end

to iterate
  set size size / 3
  hatch 1
  fd size / 2
  lt 60
  hatch 1
  fd size / 2
  rt 120
  hatch 1
  fd size / 2
  lt 60
end

to mystep [n side polygon]
  ask turtles [snowflake n side polygon]
  tick
end

to snowflake [n side polygon]
  if n = 0 [fd side stop]

  snowflake (n - 1) (side / polygon) polygon
  lt 60

  snowflake (n - 1) (side / polygon) polygon
  rt 120

  snowflake (n - 1) (side / polygon) polygon
  lt 60

  snowflake (n - 1) (side / polygon) polygon
end

to main [n side polygon]
  ask turtles [
    set heading 0
    repeat polygon [
      snowflake n side polygon
      rt 360 / polygon
    ]
  ]
end
```

---

## 3. 프로시저 설명

## 3.1 `setup`

```netlogo
to setup
  clear-all
  create-turtles 1
  [
    set heading 90
    set color blue
    pd
  ]
  reset-ticks
end
```

`setup`은 모델을 처음 실행할 때 사용하는 초기화 프로시저이다.

### 역할

1. 화면과 기존 turtle을 모두 삭제한다.
2. turtle 1마리를 생성한다.
3. turtle의 방향을 오른쪽으로 설정한다.
4. turtle의 색상을 파란색으로 설정한다.
5. 펜을 내려서 이동할 때 선이 그려지도록 한다.
6. tick 값을 초기화한다.

### 주요 명령어

| 코드 | 의미 |
|---|---|
| `clear-all` | 화면, turtle, tick 등을 모두 초기화 |
| `create-turtles 1` | turtle 1마리 생성 |
| `set heading 90` | turtle 방향을 90도로 설정 |
| `set color blue` | turtle 색상을 파란색으로 설정 |
| `pd` | pen down, 이동할 때 선을 그림 |
| `reset-ticks` | tick 값을 0으로 초기화 |

NetLogo에서 `heading`은 turtle이 바라보는 방향을 의미한다.

```text
0   → 위쪽
90  → 오른쪽
180 → 아래쪽
270 → 왼쪽
```

따라서 현재 코드의 `set heading 90`은 turtle이 오른쪽을 바라보도록 설정한다.

---

## 3.2 `step`

```netlogo
to step
  ask turtles [ iterate ]
  tick
end
```

`step`은 모든 turtle에게 `iterate`를 실행하도록 명령하는 프로시저이다.

### 역할

1. 현재 존재하는 모든 turtle에게 `iterate`를 실행시킨다.
2. 한 단계 실행 후 `tick`을 1 증가시킨다.

즉, 버튼으로 `step`을 반복 실행하면 turtle들이 계속해서 분기하며 프랙탈 구조를 만들어간다.

---

## 3.3 `iterate`

```netlogo
to iterate
  set size size / 3
  hatch 1
  fd size / 2
  lt 60
  hatch 1
  fd size / 2
  rt 120
  hatch 1
  fd size / 2
  lt 60
end
```

`iterate`는 turtle이 자기 자신과 새로 복제된 turtle들을 이용해 선을 확장하는 프로시저이다.

### 역할

1. turtle의 크기를 1/3로 줄인다.
2. turtle을 복제한다.
3. 앞으로 이동한다.
4. 방향을 바꾼다.
5. 다시 복제하고 이동한다.
6. 이 과정을 반복하여 가지처럼 퍼지는 구조를 만든다.

### 주요 명령어

| 코드 | 의미 |
|---|---|
| `set size size / 3` | turtle의 크기를 1/3로 줄임 |
| `hatch 1` | 현재 turtle과 같은 속성을 가진 turtle 1마리를 복제 |
| `fd size / 2` | 현재 turtle 크기의 절반만큼 앞으로 이동 |
| `lt 60` | 왼쪽으로 60도 회전 |
| `rt 120` | 오른쪽으로 120도 회전 |

이 방식은 turtle을 계속 복제하면서 프랙탈 구조를 만들어가는 방식이다.

---

## 4. 재귀 방식 프랙탈

## 4.1 `mystep`

```netlogo
to mystep [n side polygon]
  ask turtles [snowflake n side polygon]
  tick
end
```

`mystep`은 재귀 방식으로 프랙탈을 그리기 위한 실행용 프로시저이다.

### 매개변수

| 매개변수 | 의미 |
|---|---|
| `n` | 재귀 깊이 |
| `side` | 기본 선 길이 |
| `polygon` | 선을 나누는 기준값 |

예를 들어 다음과 같이 실행할 수 있다.

```netlogo
mystep 2 30 5
```

의미는 다음과 같다.

```text
재귀 깊이: 2
선 길이: 30
polygon 값: 5
```

---

## 4.2 `snowflake`

```netlogo
to snowflake [n side polygon]
  if n = 0 [fd side stop]

  snowflake (n - 1) (side / polygon) polygon
  lt 60

  snowflake (n - 1) (side / polygon) polygon
  rt 120

  snowflake (n - 1) (side / polygon) polygon
  lt 60

  snowflake (n - 1) (side / polygon) polygon
end
```

`snowflake`는 실제로 프랙탈 선을 그리는 핵심 재귀 프로시저이다.

### 동작 방식

`n`이 0이면 더 이상 쪼개지 않고 선을 하나 그린다.

```netlogo
if n = 0 [fd side stop]
```

즉, 이것은 재귀의 종료 조건이다.

`n`이 0보다 크면, 하나의 선을 네 개의 작은 선으로 나누어 그린다.

```netlogo
snowflake (n - 1) (side / polygon) polygon
lt 60

snowflake (n - 1) (side / polygon) polygon
rt 120

snowflake (n - 1) (side / polygon) polygon
lt 60

snowflake (n - 1) (side / polygon) polygon
```

이 구조는 코흐 곡선과 비슷하다.

```text
직선 하나
→ 더 작은 선 여러 개로 분할
→ 각 작은 선도 다시 분할
→ 반복
```

그래서 `n` 값이 커질수록 더 복잡한 프랙탈 구조가 생성된다.

---

## 5. 전체 다각형 프랙탈 그리기

## 5.1 `main`

```netlogo
to main [n side polygon]
  ask turtles [
    set heading 0
    repeat polygon [
      snowflake n side polygon
      rt 360 / polygon
    ]
  ]
end
```

`main`은 `snowflake`를 여러 번 반복하여 전체 다각형 형태의 프랙탈을 그리는 프로시저이다.

### 매개변수

| 매개변수 | 의미 |
|---|---|
| `n` | 재귀 깊이 |
| `side` | 한 변의 기본 길이 |
| `polygon` | 몇 각형으로 반복할지 결정 |

예:

```netlogo
main 2 30 5
```

의미:

```text
재귀 깊이 2
선 길이 30
5각형 구조
```

---

## 5.2 `polygon`의 역할

`polygon`은 두 가지 역할을 한다.

### 1. 전체 모양을 몇 번 반복할지 결정

```netlogo
repeat polygon [
  snowflake n side polygon
  rt 360 / polygon
]
```

예를 들어:

```text
polygon = 3 → 3번 반복 → 삼각형 구조
polygon = 4 → 4번 반복 → 사각형 구조
polygon = 5 → 5번 반복 → 오각형 구조
polygon = 6 → 6번 반복 → 육각형 구조
```

### 2. 회전 각도를 결정

```netlogo
rt 360 / polygon
```

예를 들어:

```text
polygon = 3 → 360 / 3 = 120도
polygon = 4 → 360 / 4 = 90도
polygon = 5 → 360 / 5 = 72도
polygon = 6 → 360 / 6 = 60도
```

---

## 6. `tick`의 역할

```netlogo
tick
```

`tick`은 NetLogo 모델의 시간 또는 실행 단계를 1 증가시키는 명령어이다.

예를 들어:

```netlogo
to step
  ask turtles [ iterate ]
  tick
end
```

이 코드는 `iterate` 실행이 한 번 끝날 때마다 tick 값을 1 증가시킨다.

```text
setup 실행 → ticks = 0
step 1번 실행 → ticks = 1
step 2번 실행 → ticks = 2
step 3번 실행 → ticks = 3
```

`tick`은 직접 그림을 그리는 명령은 아니지만, 모델이 몇 단계 진행되었는지 기록하는 역할을 한다.

프랙탈 그리기 예제에서는 다음과 같은 의미로 사용할 수 있다.

```text
step 또는 mystep 한 번 실행
→ 프랙탈 생성 과정이 한 단계 진행됨
→ tick 값 증가
```

---

## 7. 실행 방법

## 7.1 Command Center에서 실행

NetLogo 하단의 Command Center에 다음 명령을 입력한다.

```netlogo
setup
```

그다음 프랙탈을 그린다.

```netlogo
main 2 30 5
```

다른 예시:

```netlogo
setup
main 1 40 3
```

```netlogo
setup
main 2 30 4
```

```netlogo
setup
main 3 20 5
```

---

## 8. Interface 버튼 구성

Interface 탭에서 버튼과 슬라이더를 만들면 더 편하게 실행할 수 있다.

## 8.1 `setup` 버튼

Button을 만들고 Commands에 다음을 입력한다.

```netlogo
setup
```

## 8.2 `run` 버튼

고정값으로 실행하려면 Commands에 다음을 입력한다.

```netlogo
main 2 30 5
```

슬라이더 값을 사용하려면 다음과 같이 입력한다.

```netlogo
main level side-length polygon
```

초기화와 실행을 한 번에 하고 싶다면 다음과 같이 작성한다.

```netlogo
setup
main level side-length polygon
```

---

## 9. Slider 구성 예시

Interface 탭에서 Slider 3개를 만든다.

## 9.1 `level`

```text
Name: level
Minimum: 0
Maximum: 5
Increment: 1
Value: 2
```

`level`은 재귀 깊이를 의미한다.

```text
level = 0 → 단순 선
level = 1 → 1단계 프랙탈
level = 2 → 2단계 프랙탈
level = 3 → 더 복잡한 프랙탈
```

## 9.2 `side-length`

```text
Name: side-length
Minimum: 5
Maximum: 100
Increment: 5
Value: 30
```

`side-length`는 기본 선 길이를 의미한다.

## 9.3 `polygon`

```text
Name: polygon
Minimum: 3
Maximum: 10
Increment: 1
Value: 5
```

`polygon`은 몇 각형 구조로 반복할지를 의미한다.

---

## 10. 추천 실행값

처음에는 너무 큰 값을 사용하지 않는 것이 좋다.  
재귀 깊이가 커질수록 그려야 하는 선의 수가 빠르게 증가하기 때문이다.

| 실행 코드 | 설명 |
|---|---|
| `main 0 30 5` | 기본 오각형 구조 |
| `main 1 30 5` | 1단계 프랙탈 |
| `main 2 30 5` | 적당히 복잡한 프랙탈 |
| `main 3 30 5` | 상당히 복잡한 프랙탈 |
| `main 2 40 3` | 삼각형 기반 프랙탈 |
| `main 2 40 4` | 사각형 기반 프랙탈 |
| `main 2 30 6` | 육각형 기반 프랙탈 |

---

## 11. 주의사항

## 11.1 `polygon`은 3 이상이 적절하다

`polygon` 값이 0이면 다음 코드에서 나누기 오류가 발생할 수 있다.

```netlogo
side / polygon
rt 360 / polygon
```

따라서 `polygon`은 최소 3 이상으로 설정하는 것이 좋다.

안전하게 하려면 `main`에 다음 코드를 추가할 수 있다.

```netlogo
if polygon < 3 [
  user-message "polygon must be 3 or greater."
  stop
]
```

개선된 `main` 예시:

```netlogo
to main [n side polygon]
  if polygon < 3 [
    user-message "polygon must be 3 or greater."
    stop
  ]

  ask turtles [
    set heading 0
    repeat polygon [
      snowflake n side polygon
      rt 360 / polygon
    ]
  ]
end
```

---

## 11.2 `n` 값이 너무 크면 느려질 수 있다

`snowflake`는 재귀적으로 자기 자신을 4번 호출한다.

따라서 `n`이 커질수록 실행량이 급격히 증가한다.

```text
n = 0 → 1개 선
n = 1 → 4개 선
n = 2 → 16개 선
n = 3 → 64개 선
n = 4 → 256개 선
```

그리고 `main`에서는 이것을 `polygon`번 반복하므로 실제 선의 수는 더 많아진다.

예를 들어:

```netlogo
main 4 30 5
```

이면 대략 다음 개수의 선을 그리게 된다.

```text
5 × 4^4 = 5 × 256 = 1280개 선
```

---

## 12. 개선된 최종 코드 예시

아래는 방어 코드와 `tick`을 추가한 개선 버전이다.

```netlogo
to setup
  clear-all
  create-turtles 1
  [
    set heading 90
    set color blue
    pd
  ]
  reset-ticks
end

to step
  ask turtles [ iterate ]
  tick
end

to iterate
  set size size / 3
  hatch 1
  fd size / 2
  lt 60

  hatch 1
  fd size / 2
  rt 120

  hatch 1
  fd size / 2
  lt 60
end

to mystep [n side polygon]
  if polygon < 3 [
    user-message "polygon must be 3 or greater."
    stop
  ]

  ask turtles [
    snowflake n side polygon
  ]

  tick
end

to snowflake [n side polygon]
  if n = 0 [
    fd side
    stop
  ]

  snowflake (n - 1) (side / polygon) polygon
  lt 60

  snowflake (n - 1) (side / polygon) polygon
  rt 120

  snowflake (n - 1) (side / polygon) polygon
  lt 60

  snowflake (n - 1) (side / polygon) polygon
end

to main [n side polygon]
  if polygon < 3 [
    user-message "polygon must be 3 or greater."
    stop
  ]

  ask turtles [
    set heading 0
    repeat polygon [
      snowflake n side polygon
      rt 360 / polygon
    ]
  ]

  tick
end
```

---

## 13. 요약

이 모델은 NetLogo의 turtle을 이용하여 프랙탈 구조를 그리는 예제이다.

`iterate`는 turtle을 복제하는 `hatch` 방식으로 구조를 확장하고, `snowflake`는 재귀 호출을 통해 선을 반복적으로 분할하여 프랙탈을 생성한다.

가장 중요한 실행 프로시저는 다음과 같다.

```netlogo
setup
main 2 30 5
```

여기서:

```text
2  → 재귀 깊이
30 → 선 길이
5  → 오각형 구조
```
# NetLogo 코흐 곡선 기반 눈꽃송이 프랙탈 그리기 (위 눈꽃송이 그리기 코드 개선 버전)

## 1. 개요

이 문서는 NetLogo의 `turtle`을 이용하여 코흐 곡선과 비슷한 눈꽃송이 프랙탈을 그리는 코드에 대한 설명이다.

이 모델은 하나의 turtle을 생성한 뒤, 재귀 프로시저 `snowflake`를 사용하여 하나의 선을 반복적으로 쪼개고 회전시킨다.  
그 결과 단순한 직선이 점점 복잡한 프랙탈 구조로 변한다.

전체 눈꽃송이 모양은 `main` 프로시저에서 `snowflake`를 여러 번 반복하고 회전시키면서 만든다.

---

## 2. 전체 코드

```netlogo
to setup
  clear-all
  create-turtles 1
    [       
      set heading 90               
      set color blue
      pd
  ]
  reset-ticks
end

to mystep [n side] ; recursive Style
  ask turtles [snowflake n side]
  tick
end

to snowflake [n side]
  if n = 0 [fd side stop]

  snowflake (n - 1) (side / 3) 
  lt 60

  snowflake (n - 1) (side / 3) 
  rt 120

  snowflake (n - 1) (side / 3) 
  lt 60

  snowflake (n - 1) (side / 3) 
end

to main [n side polygon]
  ask turtles[set heading 0 repeat polygon [snowflake n side rt 360 / polygon]]
end
```

---

## 3. 실행 방법

NetLogo의 Command Center에서 다음 순서로 실행한다.

```netlogo
setup
main 2 20 3
```

위 명령의 의미는 다음과 같다.

| 값 | 의미 |
|---|---|
| `2` | 재귀 깊이 |
| `20` | 한 변의 기본 길이 |
| `3` | 3번 반복하여 삼각형 방향으로 눈꽃송이 구조 생성 |

즉, `main 2 20 3`은 재귀 깊이 2단계의 코흐 곡선 형태를 그리고, 이를 3번 회전 반복하여 눈꽃송이와 비슷한 프랙탈 구조를 만든다.

---

## 4. 프로시저 설명

## 4.1 `setup`

```netlogo
to setup
  clear-all
  create-turtles 1
    [       
      set heading 90               
      set color blue
      pd
  ]
  reset-ticks
end
```

`setup`은 모델을 처음 실행할 때 사용하는 초기화 프로시저이다.

### 역할

1. 기존 화면과 turtle을 모두 삭제한다.
2. turtle 1마리를 생성한다.
3. turtle의 방향을 90도로 설정한다.
4. turtle의 색상을 파란색으로 설정한다.
5. 펜을 내려서 이동할 때 선이 그려지도록 한다.
6. tick 값을 0으로 초기화한다.

### 주요 명령어

| 코드 | 의미 |
|---|---|
| `clear-all` | 화면, turtle, tick 등을 모두 초기화 |
| `create-turtles 1` | turtle 1마리 생성 |
| `set heading 90` | turtle의 방향을 90도로 설정 |
| `set color blue` | turtle 색상을 파란색으로 설정 |
| `pd` | pen down, turtle이 이동할 때 선을 그림 |
| `reset-ticks` | tick 값을 0으로 초기화 |

NetLogo에서 `heading` 값은 turtle이 바라보는 방향을 의미한다.

```text
0   → 위쪽
90  → 오른쪽
180 → 아래쪽
270 → 왼쪽
```

따라서 `set heading 90`은 turtle이 오른쪽을 바라보게 하는 명령이다.

---

## 4.2 `mystep`

```netlogo
to mystep [n side] ; recursive Style
  ask turtles [snowflake n side]
  tick
end
```

`mystep`은 재귀 방식으로 프랙탈 선을 한 번 그리는 실행용 프로시저이다.

### 매개변수

| 매개변수 | 의미 |
|---|---|
| `n` | 재귀 깊이 |
| `side` | 기본 선 길이 |

예를 들어 다음과 같이 실행할 수 있다.

```netlogo
setup
mystep 2 20
```

이 경우 전체 눈꽃송이 모양이 아니라, 하나의 방향으로만 프랙탈 선이 그려진다.  
전체 눈꽃송이 형태를 만들고 싶다면 `mystep`보다 `main`을 사용하는 것이 좋다.

---

## 4.3 `snowflake`

```netlogo
to snowflake [n side]
  if n = 0 [fd side stop]

  snowflake (n - 1) (side / 3) 
  lt 60

  snowflake (n - 1) (side / 3) 
  rt 120

  snowflake (n - 1) (side / 3) 
  lt 60

  snowflake (n - 1) (side / 3) 
end
```

`snowflake`는 실제로 코흐 곡선 형태의 프랙탈 선을 그리는 핵심 재귀 프로시저이다.

이 프로시저는 `n` 값에 따라 동작이 달라진다.

---

### 1. 종료 조건

```netlogo
if n = 0 [fd side stop]
```

`n`이 0이면 더 이상 선을 쪼개지 않고, 현재 방향으로 `side`만큼 앞으로 이동한다.

즉, 실제 선이 그려지는 부분은 다음 코드이다.

```netlogo
fd side
```

여기서 `fd`는 `forward`의 줄임말이며, turtle을 앞으로 이동시키는 명령이다.  
펜이 내려가 있는 상태이므로 turtle이 이동한 자리에 선이 그려진다.

---

### 2. 재귀 호출

```netlogo
snowflake (n - 1) (side / 3)
```

`n`이 0이 아니면 `snowflake`는 자기 자신을 다시 호출한다.

이때 재귀 깊이는 1 감소한다.

```netlogo
n - 1
```

그리고 선의 길이는 3으로 나누어 더 짧아진다.

```netlogo
side / 3
```

즉, 하나의 긴 선을 세 부분으로 나누고, 그 중간에 꺾임을 만들어 코흐 곡선과 비슷한 구조를 만든다.

---

### 3. 회전 구조

`snowflake` 안에서는 다음 회전 명령이 사용된다.

```netlogo
lt 60
rt 120
lt 60
```

의미는 다음과 같다.

| 코드 | 의미 |
|---|---|
| `lt 60` | 왼쪽으로 60도 회전 |
| `rt 120` | 오른쪽으로 120도 회전 |
| `lt 60` | 왼쪽으로 60도 회전 |

이 회전 구조 때문에 단순한 직선이 꺾인 선으로 바뀌며, 코흐 곡선과 비슷한 프랙탈 모양이 만들어진다.

---

## 4.4 `main`

```netlogo
to main [n side polygon]
  ask turtles[set heading 0 repeat polygon [snowflake n side rt 360 / polygon]]
end
```

`main`은 `snowflake`를 여러 번 반복하여 전체 눈꽃송이 형태를 만드는 프로시저이다.

### 역할

1. turtle의 방향을 0도로 설정한다.
2. `snowflake`를 실행하여 프랙탈 선을 하나 그린다.
3. `360 / polygon`만큼 오른쪽으로 회전한다.
4. 이 과정을 `polygon`번 반복한다.

조금 더 읽기 쉽게 펼쳐 쓰면 다음과 같다.

```netlogo
to main [n side polygon]
  ask turtles [
    set heading 0
    repeat polygon [
      snowflake n side
      rt 360 / polygon
    ]
  ]
end
```

---

## 5. 매개변수 설명

`main`은 다음과 같이 사용한다.

```netlogo
main n side polygon
```

각 매개변수의 의미는 다음과 같다.

| 매개변수 | 의미 | 예시 |
|---|---|---|
| `n` | 재귀 깊이 | `2` |
| `side` | 선의 기본 길이 | `20` |
| `polygon` | 몇 번 반복하여 전체 도형을 만들지 결정 | `3` |

예를 들어:

```netlogo
main 2 20 3
```

은 다음과 같은 의미이다.

```text
n = 2          → 재귀 깊이 2
side = 20      → 기본 선 길이 20
polygon = 3    → 3번 반복하여 삼각형 구조 생성
```

---

## 6. `polygon`의 역할

`polygon`은 `main`에서 전체 도형을 몇 번 반복하여 만들지를 결정한다.

```netlogo
repeat polygon [
  snowflake n side
  rt 360 / polygon
]
```

예를 들어:

| polygon 값 | 반복 횟수 | 회전 각도 | 결과 |
|---|---:|---:|---|
| `3` | 3번 | 120도 | 삼각형 기반 눈꽃송이 |
| `4` | 4번 | 90도 | 사각형 기반 프랙탈 |
| `5` | 5번 | 72도 | 오각형 기반 프랙탈 |
| `6` | 6번 | 60도 | 육각형 기반 프랙탈 |

이전 구조와 달리, 현재 코드에서는 `polygon`을 `snowflake` 안에서 사용하지 않는다.  
따라서 `polygon`은 선의 축소 비율에 영향을 주지 않고, 전체 도형의 반복 횟수와 회전 각도만 결정한다.

코흐 곡선의 선 분할 비율은 `snowflake` 내부에서 항상 `side / 3`으로 고정되어 있다.

---

## 7. `tick`의 역할

```netlogo
tick
```

`tick`은 NetLogo에서 모델의 시간 또는 실행 단계를 1 증가시키는 명령이다.

이 코드에서는 `mystep` 안에서 사용된다.

```netlogo
to mystep [n side]
  ask turtles [snowflake n side]
  tick
end
```

즉, `mystep`을 한 번 실행할 때마다 tick 값이 1 증가한다.

```text
setup 실행 → ticks = 0
mystep 1번 실행 → ticks = 1
mystep 2번 실행 → ticks = 2
```

`tick`은 직접 선을 그리는 명령은 아니지만, 모델이 몇 단계 실행되었는지 기록하는 역할을 한다.

---

## 8. 실행 예시

### 8.1 기본 실행

```netlogo
setup
main 2 20 3
```

재귀 깊이 2, 선 길이 20, 삼각형 구조의 코흐 눈꽃송이 프랙탈을 그린다.

---

### 8.2 단순한 구조

```netlogo
setup
main 0 20 3
```

재귀를 적용하지 않고 기본적인 삼각형 구조를 그린다.

---

### 8.3 더 복잡한 구조

```netlogo
setup
main 3 20 3
```

재귀 깊이가 3이므로 더 복잡한 눈꽃송이 프랙탈이 만들어진다.

---

### 8.4 사각형 기반 구조

```netlogo
setup
main 2 20 4
```

4번 반복하여 사각형 기반의 프랙탈 구조를 만든다.

---

### 8.5 오각형 기반 구조

```netlogo
setup
main 2 20 5
```

5번 반복하여 오각형 기반의 프랙탈 구조를 만든다.

---

### 8.6 육각형 기반 구조

```netlogo
setup
main 2 20 6
```

6번 반복하여 육각형 기반의 프랙탈 구조를 만든다.

---

## 9. Interface 버튼 구성

NetLogo의 Interface 탭에서 버튼을 만들면 더 쉽게 실행할 수 있다.

---

### 9.1 `setup` 버튼

Interface 탭에서 Button을 만들고 Commands에 다음을 입력한다.

```netlogo
setup
```

이 버튼은 모델을 초기화하고 turtle을 새로 생성한다.

---

### 9.2 `run` 버튼

고정된 값으로 실행하려면 Button의 Commands에 다음을 입력한다.

```netlogo
main 2 20 3
```

이 버튼을 누르면 재귀 깊이 2, 선 길이 20, 삼각형 구조의 눈꽃송이 프랙탈이 그려진다.

---

### 9.3 초기화와 실행을 한 번에 하는 버튼

버튼 하나로 초기화와 실행을 동시에 하고 싶다면 Commands에 다음을 입력한다.

```netlogo
setup
main 2 20 3
```

이렇게 하면 버튼 하나를 누를 때마다 화면이 초기화되고 새로운 프랙탈이 그려진다.

---

## 10. Slider를 이용한 실행

값을 직접 바꾸면서 실행하고 싶다면 Interface 탭에서 Slider를 만들 수 있다.

추천 Slider는 다음과 같다.

| Slider 이름 | 의미 | 추천 범위 | 기본값 |
|---|---|---:|---:|
| `level` | 재귀 깊이 | 0 ~ 5 | 2 |
| `side-length` | 선 길이 | 5 ~ 100 | 20 |
| `polygon` | 반복 횟수 및 전체 도형 구조 | 3 ~ 10 | 3 |

Slider를 만든 뒤, 버튼 Commands에 다음을 입력한다.

```netlogo
setup
main level side-length polygon
```

이제 Slider 값을 조절하면서 다양한 프랙탈 구조를 만들 수 있다.

---

## 11. 주의사항

## 11.1 `polygon`은 3 이상으로 설정하는 것이 좋다

`polygon` 값은 다음 코드에서 나누기에 사용된다.

```netlogo
rt 360 / polygon
```

따라서 `polygon`이 0이면 나누기 오류가 발생한다.  
또한 1이나 2는 다각형 구조로 보기 어렵기 때문에 일반적으로 3 이상을 사용하는 것이 좋다.

---

## 11.2 `n`이 너무 크면 실행이 느려질 수 있다

`snowflake`는 자기 자신을 4번 재귀 호출한다.

```netlogo
snowflake (n - 1) (side / 3)
snowflake (n - 1) (side / 3)
snowflake (n - 1) (side / 3)
snowflake (n - 1) (side / 3)
```

따라서 재귀 깊이 `n`이 커질수록 그려야 하는 선의 수가 빠르게 증가한다.

```text
n = 0 → 1개 선
n = 1 → 4개 선
n = 2 → 16개 선
n = 3 → 64개 선
n = 4 → 256개 선
```

그리고 `main`에서는 이 과정을 `polygon`번 반복한다.

예를 들어:

```netlogo
main 4 20 3
```

이면 대략 다음 개수의 선을 그리게 된다.

```text
3 × 4^4 = 3 × 256 = 768개 선
```

따라서 처음 실행할 때는 다음 정도의 값을 추천한다.

```netlogo
main 2 20 3
```

---

## 12. 개선 코드 예시

아래 코드는 `polygon` 값이 너무 작을 때 오류를 방지하는 코드를 추가한 버전이다.

```netlogo
to setup
  clear-all
  create-turtles 1
  [
    set heading 90
    set color blue
    pd
  ]
  reset-ticks
end

to mystep [n side]
  ask turtles [
    snowflake n side
  ]
  tick
end

to snowflake [n side]
  if n = 0 [
    fd side
    stop
  ]

  snowflake (n - 1) (side / 3)
  lt 60

  snowflake (n - 1) (side / 3)
  rt 120

  snowflake (n - 1) (side / 3)
  lt 60

  snowflake (n - 1) (side / 3)
end

to main [n side polygon]
  if polygon < 3 [
    user-message "polygon must be 3 or greater."
    stop
  ]

  ask turtles [
    set heading 0
    repeat polygon [
      snowflake n side
      rt 360 / polygon
    ]
  ]
end
```

---

## 13. 요약

이 NetLogo 모델은 turtle을 이용하여 코흐 곡선과 비슷한 눈꽃송이 프랙탈을 그리는 예제이다.

핵심 프로시저는 `snowflake`이다.  
`snowflake`는 하나의 선을 3등분하고, 그 과정에서 왼쪽과 오른쪽으로 회전하며 프랙탈 구조를 만든다.

전체 눈꽃송이 형태를 만들 때는 `main`을 사용한다.

```netlogo
setup
main 2 20 3
```

여기서 각 값의 의미는 다음과 같다.

```text
2  → 재귀 깊이
20 → 선 길이
3  → 삼각형 방향으로 반복
```

즉, 이 코드는 단순한 turtle 이동 명령을 재귀적으로 반복하여 복잡한 기하학적 프랙탈 구조를 생성하는 NetLogo 예제이다.
즉, 이 코드는 turtle이 선을 그리면서 반복과 재귀를 통해 점점 복잡한 기하학적 프랙탈 구조를 만들어내는 NetLogo 모델이다.
