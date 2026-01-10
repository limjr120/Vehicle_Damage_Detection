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

### 1) Algorithm

| 분류 | 꼭 공부할 알고리즘/모델 | 한 줄 핵심(무엇에 쓰나) | 장점(핵심 1개) | 주의/한계(핵심 1개) | 링크 |
|---|---|---|---|---|---|
| 문제정의/평가 | Confusion Matrix / Precision-Recall / F1 / ROC-AUC | 파손 클래스 불균형에서 성능을 제대로 해석 | 임계값·비용 관점 판단 가능 | Accuracy만 보면 착시 발생 |  |
| 문제정의/평가 | mAP(Detection), IoU | 탐지·분할 성능의 표준 지표 | 모델 간 객관적 비교 가능 | IoU threshold 설정에 민감 |  |
| 베이스라인 | ResNet (Transfer Learning) | 파손/정상 이진 분류 베이스라인 | 학습 안정적, 재현성 높음 | 미세 파손 정보 손실 가능 |  |
| 베이스라인 | EfficientNet | 파라미터 대비 성능 효율적 분류 | 성능·속도 균형 우수 | 해상도/스케일 민감 |  |
| 최신 분류 | ViT / Swin Transformer | 전역 문맥 기반 미세 파손 인식 | 성능 상한 높음 | 데이터 적으면 과적합 |  |
| 객체탐지(필수) | YOLO 계열 (v5~v8 등) | 파손 위치를 박스로 탐지 | 실시간·실무 적용 용이 | 작은 파손 탐지 어려움 |  |
| 객체탐지(비교) | Faster R-CNN | 정확도 중심 2-stage 탐지 | 소형 물체 인식 강점 | 속도 느림 |  |
| 객체탐지(비교) | RetinaNet (Focal Loss) | 불균형 데이터 대응 탐지 | 희귀 파손 탐지에 유리 | 하이퍼파라미터 민감 |  |
| 세그멘테이션 | U-Net / DeepLabV3+ | 파손 영역을 픽셀 단위 분할 | 손상 범위 추정 가능 | 마스크 라벨 비용 큼 |  |
| 세그멘테이션 | Mask R-CNN | 박스+마스크 동시 예측 | 설명력·정밀도 높음 | 연산량 큼 |  |
| 해석/디버깅 | CAM / Grad-CAM | 모델이 본 파손 위치 시각화 | 신뢰성·설명력 향상 | 정량 지표 아님 |  |
| 이상탐지(보조) | AutoEncoder / PatchCore / PaDiM | 정상 기반 파손 이상 감지 | 라벨 부족 시 유용 | 파손 유형 분류는 별도 |  |
| 학습전략 | Data Augmentation (MixUp, CutMix 등) | 촬영 조건·각도 일반화 | 성능 향상 효과 큼 | 과하면 라벨 왜곡 |  |
| 학습전략 | Class Imbalance 대응 (Focal, Weighted CE) | 파손 데이터 희소 문제 해결 | Recall 개선 | FP 증가 위험 |  |
| 학습전략 | Hard Example Mining (OHEM) | 헷갈리는 샘플 집중 학습 | 실무 체감 성능↑ | 파이프라인 복잡 |  |
| 데이터설계 | Stratified Split / Leakage 방지 | 동일 차량·사고 중복 차단 | 성능 신뢰도 확보 | 설계 미흡 시 과대평가 |  |
| 배포/운영 | Quantization / Pruning / TensorRT | 추론 속도·비용 최적화 | 실서비스 가능 | 정확도 저하 가능 |  |

### 2) Datasets

### 3) Modeling

### **Stage1)** Vehicle Detection Model

### **Stage2)** Damage Detection Model

### **Stage3)** Damage Classification Model

### **Stage4)** Damage Localization Model


## 2. Model
