# NetLogo_lab
NetLogo를 연구합니다.

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

즉, 이 코드는 turtle이 선을 그리면서 반복과 재귀를 통해 점점 복잡한 기하학적 프랙탈 구조를 만들어내는 NetLogo 모델이다.
