# 1. EDA
- 우리 데이터셋(aihub 차량파손이미지데이터)의 damaged/images, damaged/labels 정보
![aihubeda](./images/image(data_description_01).png)
![aihubeda](./images/image(data_description_02).png)

**시각화**
  
**[Case1]**
![aihubeda1](./images/imgae(week3_01).png)

**[Case2]**
![aihubeda1](./images/imgae(week3_02).png)

**[Case3]**
![aihubeda1](./images/imgae(week3_03).png)

# 2. 데이터셋 분리
- 전체 DATA 1200개 중 train/val/test를 8:1:1로 분리
- Train: 960 / Val: 120 / Test: 120

# 3. 모델링 및 테스트
- MODEL = "yolov8s.pt"
- IMGSZ = 640
- EPOCHS = 100
- BATCH = 16

## 가. 전체 성능

### Micro Average (전체 객체 기준)

| Metric | Value |
|------|------|
| Precision | **0.5304** |
| Recall | **0.3503** |
| F1-score | **0.4219** |
| TP / FP / FN | 131 / 116 / 243 |

- 실제 파손 객체 중 **약 35%만 탐지**
- 탐지된 객체의 절반 정도만 정확한 예측
- **FN(미탐지)이 매우 많음 → Recall이 핵심 병목**

### Bounding Box 품질 (TP 기준)

| Metric | Value |
|------|------|
| Mean IoU (TP only) | **0.8456** |

- 탐지에 성공한 객체에 대해서는 **박스 위치 정확도 매우 우수**
- 위치 회귀(Box Regression) 문제는 거의 없음

### Macro Average (클래스 동일 가중)

| Metric | Value |
|------|------|
| Precision | **0.5706** |
| Recall | **0.3546** |
| F1-score | **0.4350** |

- 클래스 간 성능 편차는 크지 않음
- 전반적으로 **모든 클래스에서 Recall 부족**

## 나. 클래스별 성능

| Class | TP | FP | FN | Precision | Recall | F1 |
|------|---:|---:|---:|----------:|-------:|----:|
| Crushed | 12 | 7 | 25 | 0.6316 | 0.3243 | 0.4286 |
| Scratched | 75 | 77 | 142 | 0.4934 | 0.3456 | 0.4065 |
| Breakage | 21 | 16 | 29 | 0.5676 | 0.4200 | 0.4828 |
| Separated | 23 | 16 | 47 | 0.5897 | 0.3286 | 0.4220 |

### 클래스별 해석 요약
- **Breakage**: 가장 안정적인 성능 (Recall/F1 최고)
- **Scratched**: 가장 어려운 클래스  
(경계 불명확, 면적 작음, 배경과 혼합)
- 모든 클래스에서 **미탐지(FN)가 FP보다 많음**

## 다. 종합 해석

- **강점**
- 탐지에 성공한 객체의 박스 정확도(IoU)는 매우 높음
- 특정 클래스에 국한된 실패는 아님

- **한계**
- 전체적으로 파손 객체를 충분히 찾아내지 못함
- Recall 저하로 인해 F1 및 체감 성능이 제한됨

> **요약**
> - “잡으면 정확하지만, 많이 놓치는 YOLO 모델”
> - 현 단계의 핵심 개선 포인트는 **Recall 향상**

## 라. 향후 개선 방향 (요약)

- Confidence threshold 조정 (↓)
- 작은 파손 객체 대응을 위한 이미지 해상도 및 증강 전략
- Scratched 클래스 중심 데이터 보강
- mAP(@0.5 / @0.5:0.95) 기반 추가 평가 권장

# 4.시각화
**[BEST CASE]**
![visualization](./images/best_01.jpg)
![visualization](./images/best_02.jpg)
![visualization](./images/best_03.jpg)
![visualization](./images/best_04.jpg)
![visualization](./images/best_05.jpg)
![visualization](./images/best_06.jpg)
![visualization](./images/best_07.jpg)
![visualization](./images/best_08.jpg)
![visualization](./images/best_09.jpg)
![visualization](./images/best_10.jpg)

**[WORST CASE]**
![visualization](./images/worst_01.jpg)
![visualization](./images/worst_02.jpg)
![visualization](./images/worst_03.jpg)
![visualization](./images/worst_04.jpg)
![visualization](./images/worst_05.jpg)
![visualization](./images/worst_06.jpg)
![visualization](./images/worst_07.jpg)
![visualization](./images/worst_08.jpg)
![visualization](./images/worst_09.jpg)
![visualization](./images/worst_10.jpg)
