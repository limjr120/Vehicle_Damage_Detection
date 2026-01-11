# EfficientNet

## 1. EfficientNet이란?
- **EfficientNet**은 Google에서 제안한 이미지 분류 모델
- **적은 파라미터와 연산량으로 최대 성능을 내는 것**을 목표로 설계된 CNN 계열 알고리즘
- 즉, **네트워크를 무작정 키우지 말고, 깊이·너비·해상도를 균형 있게 키우자** 는 것

---

## 2. 기존 CNN(ResNet 등)의 한계
기존 CNN들은 보통 아래 중 하나의 방식으로만 확장했다.

- 깊이만 증가 (ResNet-50 → 101 → 152)
- 채널 수(너비)만 증가
- 입력 해상도만 증가

이 방식의 문제점:
- 연산량 대비 성능 향상이 비효율적
- 모델마다 설계 기준이 경험적
- 모바일/엣지 환경에 부적합

---

## 3. EfficientNet의 핵심 아이디어: Compound Scaling

EfficientNet은 **Compound Scaling**이라는 단일 공식으로  
다음 3가지를 **동시에, 비율에 맞게 확장**한다.

- **Depth (깊이)**: 레이어 수
- **Width (너비)**: 채널 수
- **Resolution (해상도)**: 입력 이미지 크기

### 핵심 개념
> “모델을 키울 때, 한 가지만 키우지 말고  
> 깊이·너비·해상도를 함께 키워야 가장 효율적이다.”

---

## 4. EfficientNet 구조적 특징

### 4.1 기본 블록: MBConv
EfficientNet은 **MBConv (Mobile Inverted Bottleneck Convolution)** 블록을 사용한다.

MBConv 구성:
- 1×1 Conv (채널 확장)
- 3×3 또는 5×5 Depthwise Conv
- Squeeze-and-Excitation(SE)
- 1×1 Conv (채널 축소)
- Skip Connection

👉 MobileNet 계열 + ResNet 개념 결합

---

### 4.2 Squeeze-and-Excitation (SE)
- 채널별 중요도를 학습
- 중요한 특징은 강조, 불필요한 채널은 억제
- 파손 이미지처럼 **국소적 특징이 중요한 문제에 효과적**

---

## 5. EfficientNet 모델 라인업

| 모델 | 입력 해상도 | 파라미터 수(대략) | 특징 |
|---|---:|---:|---|
| EfficientNet-B0 | 224×224 | ~5.3M | 기본 모델, 빠른 베이스라인 |
| EfficientNet-B1 | 240×240 | ~7.8M | B0 대비 성능 향상 |
| EfficientNet-B2 | 260×260 | ~9.2M | 해상도 증가 |
| EfficientNet-B3 | 300×300 | ~12M | 실무에서 자주 사용 |
| EfficientNet-B4 | 380×380 | ~19M | 고성능 |
| EfficientNet-B5 | 456×456 | ~30M | 대형 모델 |
| EfficientNet-B6 | 528×528 | ~43M | 연구/서버용 |
| EfficientNet-B7 | 600×600 | ~66M | ImageNet SOTA급 |

---

## 6. ResNet vs EfficientNet 간단 비교

| 구분 | ResNet | EfficientNet |
|---|---|---|
| 설계 철학 | 깊이를 통한 성능 향상 | 효율 최적화 |
| 핵심 구조 | Residual Block | MBConv + SE |
| 스케일링 방식 | 경험적 | Compound Scaling |
| 파라미터 효율 | 보통 | 매우 높음 |
| 모바일/엣지 | 부적합 | 적합 |
| 학습 안정성 | 매우 좋음 | 좋음 |

---

## 7. 차량 파손 이미지 분류 관점에서의 활용

### 장점
- 적은 데이터에서도 성능 안정적
- 연산량 대비 정확도 우수
- 실시간/대량 추론 환경에 적합

### 주의점
- 입력 해상도가 커질수록 메모리 사용량 급증
- 미세 파손(스크래치)은 해상도 설정이 중요

---

## 8. 실무/스터디 추천 사용 전략

- **Baseline 비교용**: ResNet-18 / ResNet-50
- **효율 중심 분류 모델**: EfficientNet-B0 / B3
- **성능 중심 분류 모델**: EfficientNet-B4 이상
- **모바일/경량 서비스**: EfficientNet-B0 / B1

---

## 9. 한 문장 요약
> **EfficientNet은 “같은 연산 자원으로 가장 똑똑하게 설계된 CNN”이다.**

---

## 10. 다음 확장 학습 포인트
- EfficientNetV2 (학습 속도 개선)
- ConvNeXt와의 구조적 차이
- EfficientNet을 Backbone으로 활용한 Detection / Segmentation
