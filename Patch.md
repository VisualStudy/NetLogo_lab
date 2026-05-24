# NetLogo Patch 다루기 예제

이 문서는 NetLogo에서 `patch`를 다루는 기본 방법을 익히기 위한 교육용 예제입니다.

NetLogo에서 화면의 한 칸 한 칸을 **patch**라고 합니다.  
`turtle`이 움직이는 개체라면, `patch`는 배경이 되는 격자 칸입니다.

---

## 1. 전체 코드

```netlogo
patches-own [
  temperature
]

to setup
  ca
  
  ask patches [
    set pcolor green
  ]

  ask patch 0 0 [
    set pcolor yellow
  ]

  ask patches with [pxcor > 0] [
    set pcolor blue
  ]

  ask patches with [pycor > 0] [
    set pcolor red
  ]

  reset-ticks
end

to temp
  ca

  ask patches [
    set temperature random 100
    set pcolor scale-color red temperature 0 100
  ]

  reset-ticks
end

to ready
  ca
  
  ask patches [
    set pcolor brown 
  ]
  
  crt 1 [
    setxy 0 0
    set color blue
    set size 2
  ]

  reset-ticks
end

to go
  ask turtles [
    right random 360
    forward 1

    ask patch-here [
      set pcolor yellow
    ]
  ]

  tick
end
```

---

## 2. 코드 설명

## patches-own

```netlogo
patches-own [
  temperature
]
```

`patches-own`은 모든 patch가 자기만의 변수를 가지도록 만드는 코드입니다.

여기서는 각 patch가 `temperature`라는 변수를 가지게 됩니다.

즉, 각각의 칸마다 온도 값을 저장할 수 있습니다.

---

## 3. setup 프로시저

```netlogo
to setup
  ca
  
  ask patches [
    set pcolor green
  ]

  ask patch 0 0 [
    set pcolor yellow
  ]

  ask patches with [pxcor > 0] [
    set pcolor blue
  ]

  ask patches with [pycor > 0] [
    set pcolor red
  ]

  reset-ticks
end
```

`setup`은 patch의 색을 바꾸는 기본 예제입니다.

---

### ca

```netlogo
ca
```

`ca`는 `clear-all`의 줄임말입니다.

화면에 있는 turtle, patch 색, tick 등을 초기화합니다.

---

### 모든 patch를 초록색으로 칠하기

```netlogo
ask patches [
  set pcolor green
]
```

모든 patch에게 명령을 내려서 색을 초록색으로 바꿉니다.

`pcolor`는 patch의 색깔을 의미합니다.

---

### 가운데 patch만 노란색으로 칠하기

```netlogo
ask patch 0 0 [
  set pcolor yellow
]
```

`patch 0 0`은 좌표 `(0, 0)`에 있는 patch입니다.

즉, 화면 가운데 patch 하나만 노란색으로 바꿉니다.

---

### 오른쪽 영역을 파란색으로 칠하기

```netlogo
ask patches with [pxcor > 0] [
  set pcolor blue
]
```

`pxcor`는 patch의 x좌표입니다.

`pxcor > 0`은 x좌표가 0보다 큰 patch를 의미합니다.

즉, 화면의 오른쪽 영역을 파란색으로 칠합니다.

---

### 위쪽 영역을 빨간색으로 칠하기

```netlogo
ask patches with [pycor > 0] [
  set pcolor red
]
```

`pycor`는 patch의 y좌표입니다.

`pycor > 0`은 y좌표가 0보다 큰 patch를 의미합니다.

즉, 화면의 위쪽 영역을 빨간색으로 칠합니다.

주의할 점은 이 코드가 앞의 파란색 칠하기보다 나중에 실행되기 때문에, 오른쪽 위 영역은 최종적으로 빨간색이 됩니다.

NetLogo에서는 나중에 실행된 색 변경이 화면에 최종적으로 남습니다.

---

## 4. temp 프로시저

```netlogo
to temp
  ca

  ask patches [
    set temperature random 100
    set pcolor scale-color red temperature 0 100
  ]

  reset-ticks
end
```

`temp`는 각 patch에 임의의 온도 값을 넣고, 그 온도에 따라 색을 다르게 표현하는 예제입니다.

---

### 각 patch에 랜덤 온도 저장하기

```netlogo
set temperature random 100
```

`random 100`은 0부터 99 사이의 정수를 랜덤으로 만듭니다.

따라서 각 patch는 서로 다른 `temperature` 값을 가지게 됩니다.

---

### 온도에 따라 색 다르게 칠하기

```netlogo
set pcolor scale-color red temperature 0 100
```

`scale-color`는 숫자 값에 따라 색의 진하기를 조절하는 명령입니다.

여기서는 `temperature` 값이 낮으면 연한 빨간색 계열, 높으면 진한 빨간색 계열로 표시됩니다.

즉, 온도 지도를 시각화하는 것처럼 patch를 표현할 수 있습니다.

---

## 5. ready 프로시저

```netlogo
to ready
  ca
  
  ask patches [
    set pcolor brown 
  ]
  
  crt 1 [
    setxy 0 0
    set color blue
    set size 2
  ]

  reset-ticks
end
```

`ready`는 turtle이 움직일 준비를 하는 프로시저입니다.

---

### 모든 patch를 갈색으로 칠하기

```netlogo
ask patches [
  set pcolor brown
]
```

전체 배경 patch를 갈색으로 바꿉니다.

---

### turtle 하나 만들기

```netlogo
crt 1 [
  setxy 0 0
  set color blue
  set size 2
]
```

`crt`는 `create-turtles`의 줄임말입니다.

`turtle` 하나를 만들고, 좌표 `(0, 0)`에 배치합니다.

```netlogo
set color blue
```

turtle의 색을 파란색으로 정합니다.

```netlogo
set size 2
```

turtle의 크기를 2로 키웁니다.

---

## 6. go 프로시저

```netlogo
to go
  ask turtles [
    right random 360
    forward 1

    ask patch-here [
      set pcolor yellow
    ]
  ]

  tick
end
```

`go`는 turtle을 움직이고, turtle이 지나간 patch의 색을 바꾸는 예제입니다.

---

### turtle을 랜덤 방향으로 돌리기

```netlogo
right random 360
```

`turtle`을 0도부터 359도 사이의 랜덤한 각도만큼 오른쪽으로 회전시킵니다.

---

### turtle을 앞으로 이동시키기

```netlogo
forward 1
```

`turtle`을 현재 바라보는 방향으로 1칸 이동시킵니다.

---

### turtle이 밟고 있는 patch 색 바꾸기

```netlogo
ask patch-here [
  set pcolor yellow
]
```

`patch-here`는 turtle이 현재 서 있는 patch를 의미합니다.

즉, turtle이 지나간 자리를 노란색으로 칠합니다.

이 코드를 실행하면 turtle이 움직이면서 지나간 길이 노란색으로 표시됩니다.

---

## 7. Interface 버튼 만들기

NetLogo의 `Interface` 탭에서 버튼을 만들면 코드를 쉽게 실행할 수 있습니다.

---

### setup 버튼

| 항목 | 값 |
|---|---|
| Button name | setup |
| Commands | `setup` |
| Forever | 체크 안 함 |

---

### temp 버튼

| 항목 | 값 |
|---|---|
| Button name | temp |
| Commands | `temp` |
| Forever | 체크 안 함 |

---

### ready 버튼

| 항목 | 값 |
|---|---|
| Button name | ready |
| Commands | `ready` |
| Forever | 체크 안 함 |

---

### go 버튼

| 항목 | 값 |
|---|---|
| Button name | go |
| Commands | `go` |
| Forever | 체크함 |

`go` 버튼은 `Forever`를 체크해야 한 번 눌렀을 때 계속 실행됩니다.

다시 누르면 실행이 멈춥니다.

---

## 8. 실행 순서

### patch 색 변화 확인하기

1. `setup` 버튼을 누른다.
2. 전체 patch 색, 가운데 patch, 오른쪽 영역, 위쪽 영역이 어떻게 변하는지 확인한다.

---

### 온도 지도 확인하기

1. `temp` 버튼을 누른다.
2. 각 patch가 랜덤 온도 값을 가지고 빨간색 계열로 다르게 칠해지는지 확인한다.

---

### turtle 이동 경로 확인하기

1. `ready` 버튼을 누른다.
2. `go` 버튼을 누른다.
3. 파란 turtle이 움직이면서 지나간 patch가 노란색으로 바뀌는지 확인한다.
4. `go` 버튼을 다시 누르면 멈춘다.

---

## 9. 핵심 문법 정리

### 모든 patch에게 명령하기

```netlogo
ask patches [
  set pcolor green
]
```

---

### 특정 좌표의 patch에게 명령하기

```netlogo
ask patch 0 0 [
  set pcolor yellow
]
```

---

### 조건에 맞는 patch에게 명령하기

```netlogo
ask patches with [pxcor > 0] [
  set pcolor blue
]
```

---

### patch의 x좌표와 y좌표 사용하기

```netlogo
pxcor
pycor
```

`pxcor`는 patch의 x좌표입니다.

`pycor`는 patch의 y좌표입니다.

---

### turtle이 현재 밟고 있는 patch 사용하기

```netlogo
patch-here
```

---

### patch 전용 변수 만들기

```netlogo
patches-own [
  temperature
]
```

---

## 10. 이 예제로 배운 것

이 예제를 통해 다음 내용을 배웠습니다.

1. 모든 patch의 색을 바꾸는 방법
2. 특정 좌표의 patch를 선택하는 방법
3. 조건에 맞는 patch만 선택하는 방법
4. patch마다 변수를 저장하는 방법
5. turtle이 밟은 patch를 찾는 방법
6. turtle이 지나간 길을 patch 색으로 표시하는 방법
7. `go` 버튼을 `Forever`로 설정해서 계속 실행하는 방법

---

## 11. 연습 문제

아래 기능을 직접 추가해보세요.

### 연습 1

`turtle`이 지나간 patch를 노란색이 아니라 초록색으로 바꿔보세요.

힌트:

```netlogo
set pcolor green
```

---

### 연습 2

`turtle`을 5마리 만들고 동시에 움직이게 해보세요.

힌트:

```netlogo
crt 5 [
  setxy 0 0
  set color blue
  set size 2
]
```

---

### 연습 3

오른쪽 영역은 파란색, 왼쪽 영역은 회색으로 칠해보세요.

힌트:

```netlogo
ask patches with [pxcor < 0] [
  set pcolor gray
]
```

---

## 12. 한 줄 요약

NetLogo에서 `patch`는 화면의 한 칸이며, `ask patches`, `ask patch x y`, `patches with [...]`, `patch-here`를 사용하면 patch를 자유롭게 다룰 수 있습니다.
