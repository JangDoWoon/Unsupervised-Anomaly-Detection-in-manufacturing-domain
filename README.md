# Unsupervised-Anomaly-Detection-in-manufacturing-domain
딥러닝 이론 및 실습 수업의 프로젝트이며, Autoencoder와 GAN을 이용해 이상치 탐지를 진행하고 비교함. 그 중 Autoencoder를 이용한 이상치 탐지의 역할을 맡아 진행함. 
## 이상치 탐지
이상치 탐지는 outlier라고 불리는 예상치와 일치하지 않는 비정상적인 패턴을 식별하는 데 사용되는 기숨임. 최근에는 기존의 머신러닝 알리즘보다 우수한 성능을 보여 딥러닝 기반 이상 감지 알고리즘이 점점 인기를 끌고 있음. 따라서, 딥러닝 기반의 이상치 탐지는 불법 프래픽 흐름, 제품 결함 탐지 등 다양한 분야에서 적용되어 왔음. 일반적으로 supervised learning을 이용한 이상치 탐지가 가장 좋은 성능을 보임. 다만 업계에서 실용화하는 데는 한계가 있음. 먼저, 데이터의 레이블의 부족이지만 모델의 정확도를 높이기 위해 레이블을 만드는 것은 비용 효율적이지 않음. 다음으로는 정상 레이블과 비정상 레이블의 데이터 수의 불균형임. 이 경우 모델의 예측 정확도가 낮게 되고 따라서 산업 분야에서는 semi-supervised learning이나 unsupervised learning이 더 선호 됨.
## MVtec-ad 데이터
MVtec-ad는 산업 검사에 중점을 둔 이상치 탐지 방법을 위한 데이터 셋임. 여기에는 15개의 다른 물체 및 텍스처 범주로 구분된 1500개 이상의 고해상도 이미지가 포함되어 있음. 각 범주는 결점이 없는 training images와 다양한 결점이 있는 test images로 구성됨. 우리는 실험을 위해 bottle 데이터를 사용함.

![image](https://user-images.githubusercontent.com/67357059/146854209-9474d22a-b6d5-46a4-8d0e-9b6dfa5630c8.png)
## Autoencoder를 이용한 이상치 탐지
### Autoencoder란?
Autoencoder는 레이블이 없는 데이터 x에서 feature vector를 학습하기 위한 unsupervised learning방법임. 이는 재구성된 input을 생성하는 데 사용할 수도 있으며, 다음 두 단계로 이루어짐.
- Encoder: Input에 대해서 feature vector를 생성함
- Decoder: 파생된 식에서 원래 input 값을 되찾음
이미지를 처리하기 위해 Encoder와 Decoder가 CNN으로 구성된 CNN Autoencoder를 사용함
### Autoencoder를 이용한 이상치 탐지
![image](https://user-images.githubusercontent.com/67357059/146855466-0cdbb77a-fa32-4c1a-9e68-324691f1d45d.png)

AutoEncoder를 사용하면 데이터에 레이블이 붙이지 않고도 비정상 데이터를 탐지할 수 있음. 정상 및 비정상 이미지는 다음과 같이 훈련됨.
- 훈련 과정에서는 정상 데이터만 사용되며 autoencoder의 출력은 input이미지와 최대한 비슷하게 출력되도록 학습됨.
- Test 과정에서 비정상 데이터가 추가되면 autoencoder의 출력이 정상 데이터처럼 복원됨. 따라서 input과 output의 차이가 커져 이상치 탐지가 가능하게 됨.
- 
![image](https://user-images.githubusercontent.com/67357059/146855836-3b2964fd-b0fd-4150-86d7-472ac649f5cf.png)

