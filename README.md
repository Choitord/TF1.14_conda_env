# TF1.14_conda_env

TensorFlow 2.5.0 환경에서 Wake Word Detection 모델을 훈련하기 위한 프로젝트입니다.

## 📁 프로젝트 구조

```
TF1.14_conda_env/
├── Train_Wake_word/           # Wake Word 훈련 관련 파일들
│   ├── tf250_final.ipynb     # 메인 훈련 노트북
│   ├── audio_yesno_micro_q.cpp # xxd 변환 TFLite 모델
│   └── xxd.exe               # 바이너리 변환 유틸리티
├── ML.yaml                   # Conda 환경 설정 파일
└── README.md                 # 프로젝트 설명서
```

## 🔧 환경 설정

### ML.yaml - Conda 환경 구성

`ML.yaml` 파일은 Train_Wake_word 폴더 내 주피터 노트북을 실행하기 위한 모든 종속성을 포함한 conda 환경 설정 파일입니다.

#### 주요 특징
- **Python 버전**: 3.8.20
- **환경 이름**: ML
- **TensorFlow 버전**: 2.5.0

#### 핵심 패키지
- **머신러닝 프레임워크**
  - TensorFlow 2.5.0
  - TensorBoard 2.11.2
  - Scikit-learn 1.0.1

- **데이터 처리**
  - NumPy 1.19.5
  - Pandas 1.1.5
  - SciPy 1.10.1

- **시각화**
  - Matplotlib 3.6.0
  - Seaborn 0.12.2

- **Jupyter 환경**
  - IPython 8.12.3
  - IPykernel 6.29.5
  - Jupyter-client 8.6.3

### 환경 설치 방법

```bash
# conda 환경 생성
conda env create -f ML.yaml

# 환경 활성화
conda activate ML

# Jupyter 노트북 실행
jupyter notebook
```

## 📓 주피터 노트북 설명

### tf250_final.ipynb

Wake Word Detection 모델을 훈련하기 위한 메인 노트북입니다.

#### 주요 기능

1. **환경 설정 및 라이브러리 임포트**
   - 필요한 라이브러리 로드 (numpy, matplotlib, seaborn 등)
   - 재현 가능한 결과를 위한 랜덤 시드 설정 (42)

2. **데이터 로딩 및 전처리**
   - Google의 mini_speech_commands 데이터셋 사용
   - 'Yes'/'No' 명령어만 필터링하여 이진 분류 문제로 단순화
   - 총 2000개 샘플 중 관련 데이터만 추출

3. **데이터셋 분할**
   - **훈련 세트**: 1,600개 샘플 (80%)
   - **검증 세트**: 200개 샘플 (10%)
   - **테스트 세트**: 200개 샘플 (10%)

4. **오디오 전처리 함수**
   - `decode_audio()`: 오디오 바이너리 데이터 디코딩
   - `get_label()`: 파일 경로에서 라벨 추출
   - `get_waveform_and_label()`: 오디오 파일에서 웨이브폼과 라벨 동시 추출

#### 목적
- 음성 명령 인식을 위한 딥러닝 모델 개발
- 'Yes'와 'No' 음성 명령을 구분하는 이진 분류기 구현
- TensorFlow 2.5.0 환경에서의 오디오 처리 및 모델 훈련 실습

## 🔨 추가 파일들

### audio_yesno_micro_q.cpp
- C++ 기반 오디오 처리 코드
- 마이크로컨트롤러 환경에서의 오디오 신호 처리를 위한 구현

### xxd.exe
- 바이너리 파일을 C 배열 형태로 변환하는 유틸리티
- 임베디드 시스템에 모델을 배포할 때 사용

## 🚀 사용 방법

1. **환경 준비**
   ```bash
   conda env create -f ML.yaml
   conda activate ML
   ```

2. **노트북 실행**
   ```bash
   cd Train_Wake_word
   jupyter notebook tf250_final.ipynb
   ```

3. **모델 훈련**
   - 노트북의 셀을 순차적으로 실행
   - 데이터 로딩부터 모델 훈련까지 전체 파이프라인 실행

## 📋 요구사항

- **운영체제**: Windows (ML.yaml 경로 기준)
- **Python**: 3.8.20
- **메모리**: 최소 4GB RAM 권장
- **저장공간**: 약 2GB (데이터셋 및 모델 포함)

## 🎯 프로젝트 목표

이 프로젝트는 TensorFlow 2.5.0 환경에서 음성 인식 모델을 개발하고, 특히 Wake Word Detection 기능을 구현하는 것을 목표로 합니다. 'Yes'와 'No' 명령어 인식을 통해 기본적인 음성 명령 시스템의 기초를 다지며, 향후 더 복잡한 음성 인식 시스템으로 확장할 수 있는 기반을 제공한다..

