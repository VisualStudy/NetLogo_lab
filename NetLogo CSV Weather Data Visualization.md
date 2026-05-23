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
