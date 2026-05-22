# NetLogo 코흐 곡선 기반 눈꽃송이 프랙탈 그리기

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
