# ResNet(Residual Network)

ResNet(Residual Network)은 2015년 Microsoft Research에서 발표한 딥러닝 CNN(합성곱 신경망) 구조로, 층이 깊어질수록 학습이 어려워지는 문제를 해결하여 현대 컴퓨터 비전 모델의 기반이 되었습니다. 

### 1. 연구 배경
   - CNN 문제점: 네트워크가 깊어지면 '기울기 소실(Gradient Vanishing)' 문제로 인해 오히려 성능이 떨어지는 'Degradation Problem'이 발생
   - 원인: 기울기 소실/폭주, 최적화 난이도 증가

### 2. ResNet 핵심 개념
   - 잔차 학습 (Residual Learning) ResNet의 가장 큰 특징은 Skip Connection(Shortcut Connection)
   - 입력값 \(x\)를 출력값에 직접 더해주는 \(H(x)=F(x)+x\) 구조를 사용.
   - 모델은 입력과 출력의 차이(잔차, Residual)인 \(F(x)\)만 학습하면 되므로, 층이 매우 깊어져도 안정적인 학습이 가능

### 3. 주요 성과
   ILSVRC 2015 우승: 152개 층을 쌓은 ResNet-152 모델로 이미지 분류 대회에서 압도적인 성능을 보였습니다.
   - 깊은 층 구성: 이전의 VGG(19층), GoogleNet(22층)을 넘어 수백 개 이상의 층을 쌓을 수 있음을 증명했습니다.

### 4. 주요 버전 학습 파라미터 수에 따라 다양한 변형이 존재합니다.
   - ResNet-18 / 34: 비교적 가벼운 모델로 빠른 추론이 필요할 때 사용됩니다.
   - ResNet-50 / 101 / 152: 연산 효율을 높이기 위해 Bottleneck 구조(1x1, 3x3, 1x1 합성곱 사용)를 채택하여 성능과 속도를 모두 잡았습니다.

### 5. 관련 자원
   - 논문 원문: Deep Residual Learning for Image Recognition
   - 코드 구현: PyTorch ResNet 가이드 또는 TensorFlow ResNet API를 통해 사전 학습된 모델을 즉시 사용할 수 있습니다. 
