# 차트 카탈로그

## 1. 차트 목록과 적합한 데이터 성격

| 차트 | 가장 적합한 데이터 성격 |
|---|---|
| Line Chart (선 차트) | 시계열 |
| Bar/Column Chart (막대 차트) | 범주형 비교 |
| Stacked Bar Chart (누적 막대) | 범주형 비교 + 구성 |
| Area / Stacked Area Chart | 시계열 + 누적 규모 |
| Pie/Donut Chart | 구성/비율 (항목 적을 때) |
| Treemap | 구성/비율 + 계층 구조 |
| Sunburst Chart | 계층 구조 + 비율 |
| Histogram | 분포 |
| Box Plot | 분포 + 이상치 |
| Violin Plot | 분포 비교 |
| Scatter Plot | 상관관계 |
| Bubble Chart | 3변량 상관관계 |
| Heatmap | 매트릭스/밀도, 상관관계 매트릭스 |
| Funnel Chart | 프로세스/전환 (선형 단일 경로) |
| Sankey Diagram | 흐름/유입-유출 (다대다 관계) |
| Alluvial Diagram | 시점별 소속 변화(코호트 이동) |
| Radar/Spider Chart | 다변량 비교 (항목 소수) |
| Parallel Coordinates | 다변량 비교 (항목 다수) |
| Gauge Chart | 단일 KPI, 목표 대비 진행률 |
| Waterfall Chart | 편차/증감 분해 |
| Candlestick Chart | 금융 시계열 (OHLC) |
| Network Graph | 관계망 |
| Choropleth/Geo Map | 지리적 데이터 |
| Word Cloud | 텍스트 빈도 |
| Bullet Chart | 목표 대비 실적 (KPI 변형) |

## 2. 가로형(와이드, PPT/데스크탑 뷰) 적합도

최종 결과물은 항상 가로가 긴 직사각형 화면에 표시된다는 전제. 이 표는 `mapping-rules.md`에서 나온 후보에 **감점 방식**으로 적용한다: 데이터·의도상 맞아도 와이드 화면에서 비효율적이면 순위를 내리고, 동일 정보를 전달하는 대체 차트가 있으면 그쪽을 승격한다.

| 차트 | 적합도 | 이유 / 대응 |
|---|---|---|
| Line / Area Chart | 매우 적합 | 시간축(가로)이 길수록 유리 |
| Bar Chart (세로 막대) | 적합 | 카테고리 많아도 가로 폭에 배치 가능 |
| Bar Chart (가로 막대) | 주의 | 카테고리 많으면 세로 공간 부족 → 세로 막대나 Top-N 요약 권장 |
| Sankey Diagram | 매우 적합 | 좌→우 흐름 구조가 가로형과 태생적으로 궁합 좋음 |
| Funnel Chart | 주의 | 세로로 좁아지는 전통 형태는 위아래 여백 낭비 → 가로형(좌→우로 좁아지는) 변형 권장 |
| Pie / Donut Chart | 주의 | 원형이라 정사각형이 이상적, 좌우 여백 낭비 → 다항목이면 Stacked Bar 대체 권장 |
| Treemap | 적합 | 고정 종횡비 없이 가로 비율에 맞춰 리사이즈 가능 |
| Sunburst | 주의 | 원형 기반, Pie와 동일 문제 → Treemap 대체 권장 |
| Heatmap (Matrix) | 적합 | 행×열 비율 조정 가능, 단 행 개수 많으면 셀 짜부라짐 |
| Scatter / Bubble | 적합 | 가로 공간 넓으면 포인트 분산에 유리 |
| Box Plot / Violin Plot | 적합 | 그룹을 가로로 나열하는 구조라 확장 잘 됨 |
| Radar/Spider Chart | 부적합 | 원형+정사각형 지향 → Parallel Coordinates로 대체 권장 |
| Parallel Coordinates | 매우 적합 | 축을 가로로 나란히 배치 |
| Waterfall Chart | 적합 | 항목을 가로로 나열, 좌우 확장 가능 |
| Gauge Chart | 부적합 | 반원/원형, 여백 낭비 큼 → Bullet Chart로 대체 권장 |
| Bullet Chart | 매우 적합 | 가로 막대 기반 KPI, 이 레이아웃의 정석 |
| Choropleth Map | 보통 | 지도 형태(세계지도는 유리, 세로로 긴 국가 지도는 여백 발생) |
| Word Cloud | 보통 | 자유 형태로 채우기는 되나 정보 밀도 낮음 |

### 대체 승격 매핑 (요약)

| 원래 후보 | 와이드 화면 대체 승격 | 이유 |
|---|---|---|
| Gauge Chart | Bullet Chart | 동일 정보, 공간 효율 압도적 |
| Radar Chart | Parallel Coordinates 또는 Grouped Bar | 원형 구조 탈피 |
| Pie/Donut (다항목) | 100% Stacked Bar | 좌우 여백 제거, 항목 많아도 확장 가능 |
| Sunburst | Treemap | 계층+비율 유지하며 와이드 최적화 |
| 세로형 Funnel | 가로형 Funnel 또는 Sankey | 위아래 여백 낭비 해소 |
| 가로 막대(카테고리 多) | 세로 막대 + Top-N | 세로 공간 부족 회피 |

### 추가 고려 사항

- **범례**: 가로형은 우측 여백이 남기 쉬우므로, 범례를 우측 세로 배치하는 것이 하단 배치보다 효율적인 경우가 많다.
- **Small Multiples**: 가로 공간이 넉넉하므로 카테고리별 미니 차트를 가로로 나열하는 구성이 유리하다 (예: 지역별 미니 라인차트 여러 개를 한 줄에).
- **라벨 겹침**: 세로 여백이 적어 축/데이터 라벨이 많으면 겹치기 쉽다. 상위 항목만 라벨 표시하는 등의 규칙이 필요할 수 있다 (사전 차단보다 시각화 후 코멘트로 안내, `scan-procedure.md`의 임계치 판단 원칙 참고).
