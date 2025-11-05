# yolov8_yolov11_guide
# 🧠 YOLOv11 Complete Study Guide

이 문서는 **YOLOv11**을 처음 공부하는 초보자를 위한 정리 자료입니다.  
이전 버전인 **YOLOv8**과의 비교, 핵심 용어 정리, 설치 및 사용 예시를 모두 포함합니다.  
Ultralytics의 YOLO 시리즈를 체계적으로 이해하고 실습할 수 있도록 구성되었습니다.

---

## 🧩 목차

1. [YOLO란 무엇인가?](#yolo란-무엇인가)
2. [YOLOv8 vs YOLOv11 비교](#yolov8-vs-yolov11-비교)
3. [YOLO 핵심 용어 정리](#yolo-핵심-용어-정리)
4. [설치 및 실행 방법](#설치-및-실행-방법)


---

## 🔍 YOLO란 무엇인가?

**YOLO (You Only Look Once)** 는 객체 탐지(Object Detection) 분야에서  
가장 많이 사용되는 **실시간 딥러닝 모델** 중 하나입니다.  

YOLO는 이미지를 여러 격자로 나누고,  
각 격자에서 한 번의 연산으로 **객체 위치(Bounding Box)**와 **클래스(Class)**를 동시에 예측합니다.  
이로 인해 다른 모델보다 훨씬 빠른 속도로 동작합니다.

> ✅ YOLO는 단 한 번의 전방 연산(Forward Pass)으로 모든 객체를 탐지하기 때문에  
> 이름 그대로 "You Only Look Once"라 불립니다.

---

## ⚖️ YOLOv8 vs YOLOv11 비교

| 비교 항목 | YOLOv8 | YOLOv11 |
|------------|---------|----------|
| **출시 시기** | 2023년 1월 | 2024년 말 |
| **개발사** | Ultralytics | Ultralytics |
| **프레임워크** | PyTorch | PyTorch |
| **백본 구조 (Backbone)** | CSPDarknet 변형 구조 | **C2f-Darknet** (효율적 특징 추출) |
| **Neck 구조** | PAN/FPN | 개선된 PAN + Lightweight Fusion |
| **탐지 Head** | Decoupled Detection Head | **Unified Efficient Head** |
| **지원 작업 (Tasks)** | Detection / Segmentation / Classification | **Detection / Segmentation / Classification / Pose** |
| **mAP (정확도)** | 높음 | **YOLOv8 대비 +2~4% 향상** |
| **속도 (FPS)** | 빠름 | **더 빠름 (최적화된 아키텍처)** |
| **모델 크기** | n, s, m, l, x | n, s, m, l, x + custom 가능 |
| **Export 지원** | ONNX, TorchScript, TensorRT | **더 다양한 Export 포맷 지원** |
| **적용 분야** | 일반적인 객체 탐지 | **산업용, 로봇, 의료, IoT 등 확장** |

> 🧠 **요약:**  
> YOLOv11은 YOLOv8보다 정확도와 속도 모두 개선되었으며,  
> Pose Estimation(자세 인식)까지 지원하는 **확장형 최신 YOLO 모델**입니다.

---

## 📘 YOLO 핵심 용어 정리

| 용어 | 설명 | 예시 |
|------|------|------|
| **Object Detection** | 이미지 속 객체를 찾고 분류하는 기술 | 사람, 자동차 탐지 |
| **Bounding Box (BBox)** | 객체의 위치를 표시하는 사각형 | (x, y, w, h) 좌표 |
| **Confidence** | 탐지된 객체일 확률 (0~1) | 0.93 → 93% 확신 |
| **Class** | 객체의 종류 | 사람(person), 자동차(car) 등 |
| **IoU (Intersection over Union)** | 예측 박스와 실제 박스의 겹치는 정도 | IoU=0.8 이상이면 좋은 탐지 |
| **mAP (mean Average Precision)** | 평균 정밀도 지표 | 높을수록 정확함 |
| **NMS (Non-Max Suppression)** | 중복 박스 제거 알고리즘 | 겹치는 박스 중 하나만 남김 |
| **Anchor Box** | 예측할 박스의 크기/비율을 미리 정의한 값 | YOLOv3~v7에서 사용됨 |
| **Backbone** | 이미지의 특징을 추출하는 신경망 부분 | Darknet, CSPDarknet 등 |
| **Neck** | 여러 단계의 특징을 결합하는 부분 | FPN, PAN 구조 등 |
| **Head** | 최종 예측(좌표, 클래스)을 출력하는 부분 | Detection Head |
| **Epoch** | 학습 데이터 1회 학습 단위 | 50 epoch 학습 |
| **Batch Size** | 한 번에 학습하는 데이터 수 | batch=16 |
| **Learning Rate (LR)** | 학습 속도 조절값 | 0.001 등 |
| **Data Augmentation** | 데이터 변형으로 일반화 향상 | 회전, 뒤집기, 색상 변화 등 |

---

## ⚙️ 설치 및 실행 방법

YOLOv11은 Ultralytics 라이브러리로 간단히 설치 가능합니다.  
Python 3.8 이상, PyTorch 환경이 필요합니다.

```bash
# YOLO 설치
pip install ultralytics

# 버전 확인
yolo version

# 테스트 실행
yolo predict model=yolov11n.pt source='https://ultralytics.com/images/bus.jpg'
