# NetLogo_lab
NetLogo를 연구합니다.

# NetLogo 소개

## 1. NetLogo란?

NetLogo는 복잡한 현상과 시스템을 쉽게 모델링하고 시뮬레이션할 수 있도록 만들어진 프로그래밍 환경이다.

주로 교육, 연구, 과학 실험, 사회 현상 분석, 생태계 모델링 등에 사용된다.

NetLogo는 `turtle`, `patch`, `observer`라는 개념을 바탕으로 여러 개체들이 서로 상호작용하는 과정을 시각적으로 표현할 수 있다.

예를 들어 개미가 먹이를 찾는 과정, 바이러스가 퍼지는 과정, 사람들이 이동하는 모습, 온도 변화, 도시의 교통 흐름 등을 간단한 코드로 표현할 수 있다.

---

## 2. NetLogo의 특징

NetLogo의 가장 큰 특징은 프로그래밍 결과를 화면에서 바로 확인할 수 있다는 점이다.

일반적인 프로그래밍 언어는 코드를 작성한 뒤 결과를 숫자나 문자로 확인하는 경우가 많지만, NetLogo는 개체들이 움직이고 색이 변하는 모습을 직접 볼 수 있다.

그래서 프로그래밍을 처음 배우는 사람도 코드의 실행 결과를 직관적으로 이해할 수 있다.

또한 버튼, 슬라이더, 그래프, 모니터 같은 인터페이스 요소를 쉽게 추가할 수 있어 실험용 프로그램을 만들기에 적합하다.

---

## 3. NetLogo의 기본 구성 요소

NetLogo에는 크게 세 가지 기본 구성 요소가 있다.

- Observer
- Turtles
- Patches

---

## 3.1 Observer

Observer는 전체 세계를 바라보고 관리하는 존재이다.

프로그램을 시작하거나, 전체 환경을 초기화하거나, 여러 개체에게 명령을 내리는 역할을 한다.

예를 들어 다음과 같은 명령은 observer가 전체 모델을 관리할 때 자주 사용된다.

```netlogo
clear-all
reset-ticks
ask turtles [
  forward 1
]
```

`clear-all`은 전체 화면과 데이터를 초기화한다.

`reset-ticks`는 시간 카운터를 0으로 초기화한다.

`ask turtles`는 모든 turtle에게 특정 명령을 내린다.

---

## 3.2 Turtles

Turtle은 NetLogo 화면 위에서 움직이는 개체이다.

거북이라는 이름을 사용하지만 실제로는 사람, 동물, 자동차, 세포, 로봇 등 다양한 대상을 의미할 수 있다.

Turtle은 위치, 방향, 색깔, 크기 같은 속성을 가질 수 있으며, 앞으로 이동하거나 방향을 바꾸는 동작을 할 수 있다.

예시는 다음과 같다.

```netlogo
crt 1 [
  set color blue
  set size 2
  setxy 0 0
]
```

위 코드는 화면 중앙에 파란색 turtle 1개를 생성한다.

---

## 3.3 Patches

Patch는 NetLogo 세계를 이루는 작은 칸이다.

화면 전체는 여러 개의 patch로 나뉘어 있으며, 각 patch는 고유한 좌표와 색깔을 가진다.

Patch는 땅, 바다, 길, 온도 분포, 감염 지역 등 공간적인 정보를 표현할 때 자주 사용된다.

예시는 다음과 같다.

```netlogo
ask patches [
  set pcolor green
]
```

위 코드는 모든 patch의 색을 초록색으로 바꾼다.

---

## 4. NetLogo의 기본 명령어

NetLogo에서 자주 사용하는 기본 명령어는 다음과 같다.

| 명령어 | 의미 |
|---|---|
| `clear-all` 또는 `ca` | 화면과 데이터를 모두 초기화한다. |
| `reset-ticks` | 시간 카운터를 0으로 초기화한다. |
| `tick` | 시간 카운터를 1 증가시킨다. |
| `crt n` | turtle을 n개 생성한다. |
| `ask` | 특정 개체에게 명령을 내린다. |
| `set` | 변수나 속성 값을 설정한다. |
| `forward n` 또는 `fd n` | turtle을 앞으로 n만큼 이동시킨다. |
| `right n` 또는 `rt n` | turtle을 오른쪽으로 n도 회전시킨다. |
| `left n` 또는 `lt n` | turtle을 왼쪽으로 n도 회전시킨다. |
| `setxy x y` | turtle의 위치를 x, y 좌표로 이동시킨다. |
| `patch-here` | turtle이 현재 위치한 patch를 의미한다. |
| `pcolor` | patch의 색을 의미한다. |
| `color` | turtle의 색을 의미한다. |

---

## 5. 간단한 NetLogo 예제

아래 코드는 turtle 하나를 만들고, 버튼을 누를 때마다 무작위 방향으로 움직이게 하는 예제이다.

```netlogo
to setup
  clear-all

  ask patches [
    set pcolor green
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

## 6. 코드 설명

## 6.1 setup 절차

```netlogo
to setup
```

`setup`은 모델을 처음 시작할 때 실행하는 절차이다.

```netlogo
clear-all
```

기존 화면과 데이터를 모두 지운다.

```netlogo
ask patches [
  set pcolor green
]
```

모든 patch의 색을 초록색으로 바꾼다.

```netlogo
crt 1 [
  setxy 0 0
  set color blue
  set size 2
]
```

turtle 1개를 만들고 화면 중앙에 배치한다.

색은 파란색, 크기는 2로 설정한다.

```netlogo
reset-ticks
```

시간 카운터를 0으로 초기화한다.

---

## 6.2 go 절차

```netlogo
to go
```

`go`는 모델이 반복적으로 실행될 때 사용하는 절차이다.

```netlogo
ask turtles [
  right random 360
  forward 1
]
```

모든 turtle에게 무작위 방향으로 회전한 뒤 앞으로 1만큼 이동하라고 명령한다.

```netlogo
ask patch-here [
  set pcolor yellow
]
```

turtle이 현재 위치한 patch의 색을 노란색으로 바꾼다.

```netlogo
tick
```

시간을 1만큼 증가시킨다.

---

## 7. 버튼으로 실행하기

NetLogo에서 위 코드를 실행하려면 Interface 화면에서 버튼을 만든다.

---

## 7.1 setup 버튼 만들기

1. Interface 탭으로 이동한다.
2. Button을 추가한다.
3. Commands에 다음을 입력한다.

```netlogo
setup
```

4. 버튼 이름을 `setup`으로 설정한다.

이 버튼을 누르면 화면이 초기화되고 turtle이 생성된다.

---

## 7.2 go 버튼 만들기

1. Button을 하나 더 추가한다.
2. Commands에 다음을 입력한다.

```netlogo
go
```

3. 버튼 이름을 `go`로 설정한다.
4. Forever 옵션을 체크하면 버튼을 한 번 눌렀을 때 `go`가 계속 반복 실행된다.

Forever 옵션을 체크하지 않으면 버튼을 누를 때마다 `go`가 한 번씩만 실행된다.

---

## 8. NetLogo 실행 흐름

위 예제의 실행 흐름은 다음과 같다.

1. `setup` 버튼을 누른다.
2. 전체 화면이 초기화된다.
3. 모든 patch가 초록색으로 바뀐다.
4. 화면 중앙에 파란색 turtle이 생성된다.
5. `go` 버튼을 누른다.
6. turtle이 무작위 방향으로 움직인다.
7. turtle이 지나간 patch가 노란색으로 바뀐다.
8. `tick`이 증가하면서 시간이 흐른다.

---

## 9. NetLogo를 배우는 이유

NetLogo는 프로그래밍 문법을 배우는 것뿐만 아니라, 복잡한 현상을 단계적으로 이해하는 데 도움이 된다.

특히 다음과 같은 사고력을 기를 수 있다.

- 복잡한 문제를 작은 개체로 나누어 보는 능력
- 개체 간 상호작용을 이해하는 능력
- 반복과 조건을 활용해 규칙을 만드는 능력
- 시뮬레이션 결과를 관찰하고 해석하는 능력
- 데이터와 그래프를 이용해 현상을 분석하는 능력

따라서 NetLogo는 단순히 코딩을 배우는 도구가 아니라, 컴퓨팅 사고력과 과학적 탐구 능력을 함께 기를 수 있는 교육용 프로그래밍 환경이라고 할 수 있다.

---

## 10. NetLogo 활용 예시

NetLogo는 다양한 분야에서 활용될 수 있다.

| 분야 | 활용 예시 |
|---|---|
| 생태계 | 포식자와 먹이 관계 시뮬레이션 |
| 보건 | 감염병 확산 모델링 |
| 사회 | 군중 행동, 여론 변화 분석 |
| 경제 | 시장 거래, 소비자 행동 분석 |
| 환경 | 산불 확산, 오염 물질 이동 |
| 교육 | 알고리즘, 반복문, 조건문 학습 |
| 인공지능 | 에이전트 기반 모델링 실험 |

---

## 11. NetLogo와 일반 프로그래밍 언어의 차이

NetLogo는 일반적인 프로그래밍 언어와 비교했을 때 시각적이고 실험적인 성격이 강하다.

| 구분 | 일반 프로그래밍 언어 | NetLogo |
|---|---|---|
| 결과 확인 | 주로 문자, 숫자, 파일 출력 | 화면에서 개체 움직임으로 확인 |
| 주요 대상 | 변수, 함수, 객체 | turtle, patch, observer |
| 학습 방식 | 문법 중심 | 시뮬레이션 중심 |
| 장점 | 다양한 프로그램 개발 가능 | 복잡한 현상을 쉽게 시각화 |
| 활용 | 웹, 앱, 서버, 시스템 개발 | 교육, 연구, 모델링, 시뮬레이션 |

---

## 12. NetLogo에서 중요한 사고방식

NetLogo를 사용할 때는 하나의 큰 문제를 작은 개체들의 행동으로 나누어 생각하는 것이 중요하다.

예를 들어 감염병 확산 모델을 만든다고 하면 다음과 같이 나누어 생각할 수 있다.

- 사람을 turtle로 표현한다.
- 공간을 patch로 표현한다.
- 감염 여부를 turtle의 색으로 표현한다.
- turtle들이 이동하면서 서로 접촉하도록 만든다.
- 감염된 turtle과 가까운 turtle이 일정 확률로 감염되도록 한다.
- 시간이 지남에 따라 감염자 수를 그래프로 표시한다.

이처럼 NetLogo는 복잡한 현상을 개체, 공간, 규칙, 시간의 흐름으로 나누어 표현하는 데 적합하다.

---

## 13. 정리

NetLogo는 여러 개체가 움직이고 상호작용하는 과정을 쉽게 표현할 수 있는 시뮬레이션 프로그래밍 도구이다.

Observer는 전체 세계를 관리하고, turtles는 움직이는 개체를 나타내며, patches는 공간을 구성하는 작은 칸을 의미한다.

NetLogo를 사용하면 복잡한 현상을 시각적으로 관찰할 수 있고, 프로그래밍의 기본 개념인 변수, 반복, 조건, 함수, 객체 개념을 자연스럽게 익힐 수 있다.

따라서 NetLogo는 프로그래밍 입문자뿐만 아니라, 과학적 탐구와 컴퓨팅 사고력을 기르고 싶은 사람에게도 유용한 도구이다.

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

# NetLogo CSV Weather Data Visualization

NetLogo에서 CSV 파일을 읽어온 뒤, 온도와 습도 데이터를 그래프로 시각화하는 프로젝트입니다.

이 프로젝트는 `weather_20260521.csv` 파일을 읽고, CSV 안에 있는 `temp`, `hum` 값을 NetLogo의 Plot에 표시합니다.

---

## 1. 프로젝트 목표

이 프로젝트의 목표는 다음과 같습니다.

- NetLogo에서 CSV 파일 읽기
- CSV 데이터의 첫 번째 제목 행 제거하기
- 온도 데이터 그래프로 시각화하기
- 습도 데이터 그래프로 시각화하기
- 하나의 Plot에서 온도와 습도 변화를 함께 확인하기

---

## 2. 사용한 CSV 파일 구조

사용한 CSV 파일 이름은 다음과 같습니다.

```text
weather_20260521.csv
```

CSV 파일은 다음과 같은 구조입니다.

```csv
index,temp,hum
1,19,85
2,18,85
3,18,85
4,17,90
5,17,95
...
```

각 열의 의미는 다음과 같습니다.

| 열 이름 | 의미 |
|---|---|
| `index` | 데이터 순서 또는 시간 순서 |
| `temp` | 온도 |
| `hum` | 습도 |

즉, `index`는 x축 값으로 사용하고, `temp`와 `hum`은 y축 값으로 사용합니다.

---

## 3. NetLogo Interface 설정

NetLogo에서 새 모델을 만든 뒤, Interface 탭에서 다음 요소를 추가합니다.

### 3.1 Button 만들기

Interface 탭에서 버튼을 하나 만들고, Commands에 다음을 입력합니다.

```netlogo
setup
```

이 버튼을 누르면 CSV 파일을 읽고 그래프를 그립니다.

---

### 3.2 Plot 만들기

Interface 탭에서 Plot을 하나 만듭니다.

Plot 이름은 반드시 다음과 같이 설정합니다.

```text
Weather Plot
```

코드에서 이 이름을 사용하기 때문에 대소문자와 띄어쓰기가 정확히 같아야 합니다.

---

### 3.3 Plot Pen 설정

`Weather Plot` 안에 Pen을 두 개 만듭니다.

```text
temperature
humidity
```

각 Pen의 의미는 다음과 같습니다.

| Pen 이름 | 의미 |
|---|---|
| `temperature` | 온도 그래프 |
| `humidity` | 습도 그래프 |

`Show legend` 옵션을 켜면 그래프에서 어떤 선이 온도이고 어떤 선이 습도인지 확인할 수 있습니다.

---

### 3.4 Plot 축 설정

그래프를 보기 쉽게 하기 위해 다음과 같이 설정합니다.

```text
X min: 0
X max: 24

Y min: 0
Y max: 100
```

또한 y축 범위가 자동으로 바뀌지 않도록 다음 옵션은 해제하는 것이 좋습니다.

```text
Auto scale y-axis? 체크 해제
```

이렇게 하면 온도와 습도 값을 0부터 100 사이에서 안정적으로 비교할 수 있습니다.

---

## 4. NetLogo 전체 코드

아래 코드를 NetLogo의 Code 탭에 입력합니다.

```netlogo
extensions [csv]

globals [
  weather-data
]

to setup
  clear-all

  ; Read CSV file
  set weather-data csv:from-file "weather_20260521.csv"

  ; Remove header row: index,temp,hum
  set weather-data but-first weather-data

  ; Select plot
  set-current-plot "Weather Plot"
  clear-plot

  ; Fix graph range for easier reading
  set-plot-x-range 0 24
  set-plot-y-range 0 100

  ; Draw temperature graph
  set-current-plot-pen "temperature"
  foreach weather-data [
    row ->
    let x item 0 row
    let temp item 1 row
    plotxy x temp
  ]

  ; Draw humidity graph
  set-current-plot-pen "humidity"
  foreach weather-data [
    row ->
    let x item 0 row
    let hum item 2 row
    plotxy x hum
  ]

  reset-ticks
end
```

---

## 5. 코드 설명

### 5.1 CSV 확장 불러오기

```netlogo
extensions [csv]
```

CSV 파일을 읽기 위해 NetLogo의 CSV 확장을 사용합니다.

---

### 5.2 전역 변수 선언

```netlogo
globals [
  weather-data
]
```

`weather-data`는 CSV 파일에서 읽어온 전체 데이터를 저장하는 변수입니다.

---

### 5.3 setup 명령 정의

```netlogo
to setup
```

`setup`은 버튼을 눌렀을 때 실행되는 명령입니다.

---

### 5.4 기존 상태 초기화

```netlogo
clear-all
```

기존 그래프, 거북이, 패치, ticks 등을 모두 초기화합니다.

이번 프로젝트에서는 거북이를 사용하지 않지만, 그래프를 새로 그리기 위해 초기화 과정이 필요합니다.

---

### 5.5 CSV 파일 읽기

```netlogo
set weather-data csv:from-file "weather_20260521.csv"
```

`weather_20260521.csv` 파일을 읽어 `weather-data` 변수에 저장합니다.

CSV 파일이 다음과 같다면,

```csv
index,temp,hum
1,19,85
2,18,85
3,18,85
```

NetLogo에서는 대략 다음과 같은 리스트 형태로 저장됩니다.

```netlogo
[
  ["index" "temp" "hum"]
  [1 19 85]
  [2 18 85]
  [3 18 85]
]
```

---

### 5.6 첫 번째 제목 행 제거

```netlogo
set weather-data but-first weather-data
```

CSV의 첫 줄은 실제 데이터가 아니라 제목입니다.

```csv
index,temp,hum
```

그래프에는 숫자 데이터만 찍어야 하므로 첫 줄을 제거합니다.

제거 전:

```netlogo
[
  ["index" "temp" "hum"]
  [1 19 85]
  [2 18 85]
]
```

제거 후:

```netlogo
[
  [1 19 85]
  [2 18 85]
]
```

---

### 5.7 Plot 선택

```netlogo
set-current-plot "Weather Plot"
```

현재 사용할 그래프를 `Weather Plot`으로 지정합니다.

이 코드를 사용하려면 Interface 탭에 있는 Plot 이름도 반드시 `Weather Plot`이어야 합니다.

---

### 5.8 Plot 초기화

```netlogo
clear-plot
```

기존에 그려진 그래프를 지웁니다.

`setup` 버튼을 여러 번 눌러도 그래프가 겹치지 않도록 하기 위해 사용합니다.

---

### 5.9 그래프 범위 고정

```netlogo
set-plot-x-range 0 24
set-plot-y-range 0 100
```

x축과 y축의 범위를 고정합니다.

이번 CSV 데이터는 `index`가 시간 순서처럼 사용되고, 온도와 습도는 0부터 100 사이의 값으로 볼 수 있으므로 y축을 `0~100`으로 고정했습니다.

---

### 5.10 온도 그래프 그리기

```netlogo
set-current-plot-pen "temperature"
```

`temperature`라는 Pen을 선택합니다.

이후에 찍는 점들은 온도 그래프로 표시됩니다.

```netlogo
foreach weather-data [
  row ->
  let x item 0 row
  let temp item 1 row
  plotxy x temp
]
```

CSV 한 줄이 다음과 같다고 하면,

```netlogo
[1 19 85]
```

각 값의 의미는 다음과 같습니다.

```text
item 0 row = 1   ; index
item 1 row = 19  ; temp
item 2 row = 85  ; hum
```

따라서 온도 그래프는 다음과 같은 방식으로 그려집니다.

```netlogo
plotxy 1 19
```

즉, x축 1 위치에 y값 19를 찍습니다.

---

### 5.11 습도 그래프 그리기

```netlogo
set-current-plot-pen "humidity"
```

이번에는 `humidity`라는 Pen을 선택합니다.

```netlogo
foreach weather-data [
  row ->
  let x item 0 row
  let hum item 2 row
  plotxy x hum
]
```

CSV 한 줄이 다음과 같다면,

```netlogo
[1 19 85]
```

습도 값은 `item 2 row`입니다.

따라서 다음과 같이 그래프에 찍힙니다.

```netlogo
plotxy 1 85
```

즉, x축 1 위치에 y값 85를 찍습니다.

---

### 5.12 ticks 초기화

```netlogo
reset-ticks
```

NetLogo의 시간 단위인 `ticks`를 0으로 초기화합니다.

이번 프로젝트는 실시간 시뮬레이션이 아니라 CSV 데이터를 한 번에 시각화하는 방식이므로 ticks가 핵심은 아니지만, `setup` 명령의 마무리로 자주 사용됩니다.

---

## 6. 실행 방법

실행 순서는 다음과 같습니다.

1. NetLogo에서 새 모델을 만든다.
2. Code 탭에 전체 코드를 붙여넣는다.
3. Interface 탭에서 `Weather Plot`을 만든다.
4. `Weather Plot` 안에 `temperature`, `humidity` Pen을 만든다.
5. Interface 탭에서 `setup` 버튼을 만든다.
6. `weather_20260521.csv` 파일을 `.nlogo` 파일과 같은 폴더에 둔다.
7. `setup` 버튼을 누른다.
8. 온도와 습도 그래프를 확인한다.

---

## 7. 결과 해석

이 프로젝트에서는 CSV 파일에 이미 저장된 데이터를 읽어와 한 번에 그래프로 표시합니다.

따라서 `setup` 버튼을 누르면 그래프가 생성되고, 그 이후에는 실시간으로 값이 변하지 않습니다.

즉, 이 프로젝트는 실시간 시뮬레이션이라기보다는 다음에 가깝습니다.

```text
저장된 날씨 데이터 시각화
```

그래프에서 확인할 수 있는 내용은 다음과 같습니다.

- 온도가 올라가는 구간
- 온도가 내려가는 구간
- 습도가 올라가는 구간
- 습도가 내려가는 구간
- 온도와 습도의 관계

일반적으로 온도와 상대습도는 반대로 움직이는 경향이 있습니다.

```text
온도 상승 → 상대습도 하락
온도 하락 → 상대습도 상승
```

이번 데이터에서도 온도가 높아질수록 습도는 낮아지는 경향을 확인할 수 있습니다.

---

## 8. 자주 발생하는 문제

### 8.1 그래프가 안 나오는 경우

다음 항목을 확인합니다.

- `setup` 버튼을 눌렀는가?
- CSV 파일이 `.nlogo` 파일과 같은 폴더에 있는가?
- Plot 이름이 정확히 `Weather Plot`인가?
- Pen 이름이 정확히 `temperature`, `humidity`인가?
- Code 탭에서 Check를 눌렀을 때 오류가 없는가?

---

### 8.2 Plot 이름 오류

코드에는 다음과 같이 되어 있습니다.

```netlogo
set-current-plot "Weather Plot"
```

따라서 Interface 탭의 Plot 이름도 반드시 다음과 같아야 합니다.

```text
Weather Plot
```

다음과 같이 다르면 오류가 발생할 수 있습니다.

```text
weather plot
Weather plot
WeatherPlot
```

---

### 8.3 Pen 이름 오류

코드에는 다음 Pen 이름이 사용됩니다.

```netlogo
set-current-plot-pen "temperature"
set-current-plot-pen "humidity"
```

따라서 Plot 안에 다음 Pen이 반드시 있어야 합니다.

```text
temperature
humidity
```

---

### 8.4 CSV 파일 위치 오류

코드에는 다음과 같이 되어 있습니다.

```netlogo
csv:from-file "weather_20260521.csv"
```

따라서 `weather_20260521.csv` 파일은 NetLogo 모델 파일과 같은 폴더에 있어야 합니다.

예시:

```text
NetLogoWeatherProject/
├─ weather-model.nlogo
├─ weather_20260521.csv
└─ README.md
```

---

## 9. World 화면에 대한 설명

NetLogo를 새로 만들면 기본적으로 검은색 World 화면이 있습니다.

이 화면은 원래 거북이, 패치, 링크 같은 에이전트가 움직이는 공간입니다.

하지만 이번 프로젝트는 거북이를 움직이는 시뮬레이션이 아니라 CSV 데이터를 Plot으로 시각화하는 프로젝트입니다.

따라서 World 화면은 크게 필요하지 않습니다.

삭제할 수는 없지만, Interface 탭에서 작게 줄여두고 Plot을 크게 배치하면 됩니다.

---

## 10. 최종 정리

이 프로젝트의 핵심 흐름은 다음과 같습니다.

```text
CSV 파일 준비
→ NetLogo에서 CSV 확장 불러오기
→ csv:from-file로 CSV 읽기
→ but-first로 제목 행 제거
→ set-current-plot으로 Plot 선택
→ set-current-plot-pen으로 Pen 선택
→ plotxy로 온도와 습도 값 찍기
→ Weather Plot에서 그래프 확인
```

이 프로젝트를 통해 NetLogo에서도 외부 CSV 데이터를 읽고, 데이터를 그래프로 시각화할 수 있음을 확인할 수 있습니다.

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
