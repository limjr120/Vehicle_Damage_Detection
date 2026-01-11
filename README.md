# Vehicle Damage Detection Study (차량 파손 여부 판별 스터디)

차량 이미지로부터 **파손 여부(damaged vs normal)** 를 판별하는 모델을 만드는 스터디 레포

---

## 0. Goals (목표)
- 이미지가 주어졌을때 차량 파손여부와 파손종류, 파손부위 등을 판단하는 모델을 구축하기 위해 아래 단계로 모델 구축
  
  **Stage1**: Vehicle Detection Model(차량인지 여부를 판단하는 모델)  
  **Stage2**: Damage Detection Model(차량에 손상이 있는지를 판단하는 모델)  
  **Stage3**: Damage Classification Model(손상 종류가 무엇인지 판단하는 모델)  
  **Stage4**: Damage Localization Model(손상 부위가 어디인지 판단하는 모델 구축)

---

## 1. Study Contents

### 1) Architecture

| 유형 | 명칭 | 발표 연도 | 핵심 아이디어 | 상세설명 |
|---|---|---:|---|---|
| 이미지 분류 | ResNet | 2015 | Skip Connection(Residual Learning)을 도입해 깊은 CNN에서도 학습 안정성 확보, Degradation 문제 해결 | [상세보기](./01.Study_Contents/Architecture/ResNet/README.md) |
| 이미지 분류 | EfficientNet | 2019 | 깊이·너비·해상도를 동시에 균형 있게 확장하는 **Compound Scaling**으로 연산 효율 극대화 | [상세보기](./01.Study_Contents/Architecture/EfficientNet/README.md) |
| 이미지 분류 | RegNet | 2020 | CNN 채널·깊이 설계를 수식으로 정의해 예측 가능한 고효율 backbone 제시 |  |
| 이미지 분류 | Vision Transformer (ViT) | 2020 | 이미지를 패치 단위 토큰으로 변환해 **Transformer Encoder**로 전역 관계를 직접 학습 | [상세보기](./01.Study_Contents/Architecture/Vision_Transformer/README.md) |
| 이미지 분류 / 탐지 / 세그 | Swin Transformer | 2021 | 윈도우 기반 Self-Attention으로 계산량을 줄이고, CNN처럼 계층적(stage) 구조 유지 |  |
| 이미지 분류 | EfficientNetV2 | 2021 | **Fused-MBConv + Progressive Learning**으로 학습 속도와 효율을 동시에 개선 | [상세보기](./01.Study_Contents/Architecture/EfficientNetV2/README.md) |
| 이미지 분류 | DeiT (Data-efficient ViT) | 2021 | 지식 증류를 통해 대규모 데이터 없이 ViT 학습 가능 |  |
| 이미지 분류 | ConvNeXt | 2022 | ResNet 구조를 유지하면서 Transformer 학습 전략을 적용해 CNN SOTA 달성 |  |
| 이미지 분류 | MaxViT | 2022 | CNN과 Window/Global Attention을 결합한 Hybrid Transformer |  |
| 객체 탐지 | YOLO (You Only Look Once) | 2016 | 객체 탐지를 하나의 end-to-end 회귀 문제로 정의해 **실시간 객체 탐지** 달성 |  |
| 객체 탐지 / 세그 | Mask R-CNN | 2017 | 객체 탐지와 픽셀 단위 마스크를 동시에 수행하는 2-stage 구조 |  |
| 세그멘테이션 | U-Net | 2015 | Encoder–Decoder 구조와 Skip Connection으로 위치 정보와 의미 정보를 결합한 픽셀 단위 분할 |  |
| 세그멘테이션 | DeepLabV3+ | 2018 | Atrous Convolution으로 다중 해상도 문맥 정보를 효과적으로 통합 |  |

### 2) Datasets

| 구분 | 폴더명 | 데이터수 | 출처 | 데이터EDA |
|---|---|---|---|---|
| non_vehicle | background |  |  |   |
| normal_vehicle | normal |  |  |  |
| normal_vehicle | normal(kaggle_dataset) |  |  |  |
| damaged_vehicle | damaged |  |  |  |


### 3) Modeling

### **Stage1)** Vehicle Detection Model

### **Stage2)** Damage Detection Model

### **Stage3)** Damage Classification Model

### **Stage4)** Damage Localization Model


## 2. Model
