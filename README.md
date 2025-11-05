# yolov8_yolov11_guide
# 🚀 YOLOv11 Study & Practice Guide

이 저장소는 **YOLOv11**을 중심으로 객체 탐지(Object Detection) 기술을 학습하고 실습한 내용을 정리한 것입니다.  
이전 버전인 **YOLOv8**과 비교하면서 차이점과 개선점을 이해하고, 실제 데이터로 모델을 훈련하는 과정을 기록합니다.

---

## 📂 프로젝트 구조

```bash
YOLOv11-Study/
│
├── 📁 data/               # 데이터셋 저장 폴더 (예: train, val, test)
│   ├── images/
│   └── labels/
│
├── 📁 notebooks/          # 학습 실습용 노트북 파일 (.ipynb)
│   ├── yolo_train.ipynb
│   └── yolo_predict.ipynb
│
├── 📁 results/            # 학습 결과 (모델, 그래프, 예측 이미지 등)
│
├── 📁 configs/            # 설정 파일 (yaml)
│   └── custom_data.yaml
│
├── 📜 requirements.txt    # 필요한 라이브러리 목록
└── 📘 README.md           # 본 문서
# 1️⃣ 필수 패키지 설치
pip install ultralytics

# 2️⃣ 버전 확인
yolo version

# 3️⃣ YOLOv11 테스트
yolo predict model=yolov11n.pt source='https://ultralytics.com/images/bus.jpg'
# 예시: 나만의 데이터셋 학습
yolo detect train data=configs/custom_data.yaml model=yolov11n.pt epochs=50 imgsz=640 batch=16
# 성능 평가
yolo detect val model=runs/detect/train/weights/best.pt data=configs/custom_data.yaml

# 예측 실행
yolo detect predict model=runs/detect/train/weights/best.pt source=data/images/test.jpg
# ONNX로 내보내기
yolo export model=runs/detect/train/weights/best.pt format=onnx

# TensorRT 변환
yolo export model=runs/detect/train/weights/best.pt format=engine
