# yolov8_yolov11_guide
# 🧠 YOLOv11 Study Note

이 저장소는 **YOLOv11**을 공부하며 정리한 내용을 담고 있습니다.  
YOLO 시리즈는 이미지나 영상 속 객체를 빠르고 정확하게 탐지(Object Detection)하는 딥러닝 모델입니다.

---

## 📌 1. YOLOv8 vs YOLOv11 비교

| 비교 항목 | YOLOv8 | YOLOv11 |
|------------|---------|----------|
| **출시 시기** | 2023년 1월 (Ultralytics) | 2024년 말 (Ultralytics) |
| **기반 프레임워크** | PyTorch | PyTorch (개선된 구조 및 훈련 효율) |
| **모델 구조** | CSPDarknet 기반 Backbone | 새로 설계된 **C2f-Darknet** 구조 |
| **성능 향상** | YOLOv5 대비 속도/정확도 개선 | YOLOv8 대비 **mAP↑, 속도↑, 파라미터↓** |
| **지원 작업(Task)** | Detection, Segmentation, Classification | Detection, Segmentation, Classification, Pose 등 |
| **Train 스크립트** | `yolo detect train ...` | 동일 (`yolo detect train ...`) |
| **추론 속도** | 빠름 | **더 빠름 (최적화된 ONNX, TensorRT 지원)** |
| **활용성** | 다양한 커뮤니티, 풍부한 예제 | 최신 버전으로 향상된 API 및 GUI 지원 |
| **적용 예시** | 차량, 사람, 동물 탐지 | 의료, 로봇, 산업용 등 확장 가능 |

> 🔍 **요약:** YOLOv11은 YOLOv8의 속도와 정확도를 모두 개선한 최신 버전으로,  
> 경량화된 구조와 다양한 작업(Task)에 대한 지원이 강화되었습니다.

---

## 📖 2. YOLO에서 자주 쓰이는 용어 정리

| 용어 | 뜻 | 설명 |
|------|-----|------|
| **Bounding Box (BBox)** | 경계 상자 | 객체의 위치를 표시하는 사각형 |
| **Confidence** | 신뢰도 | 탐지된 객체일 확률 (0~1 사이 값) |
| **Class** | 분류 | 어떤 종류의 객체인지 (예: 사람, 자동차 등) |
| **IoU (Intersection over Union)** | 교집합 비율 | 예측된 박스와 실제 박스의 겹치는 정도 |
| **mAP (mean Average Precision)** | 평균 정밀도 | 모델의 전체 탐지 정확도를 나타내는 지표 |
| **NMS (Non-Max Suppression)** | 비최대 억제 | 중복 박스 제거 알고리즘 |
| **Anchor** | 기준 박스 | 예측할 박스의 크기와 비율을 미리 정해둔 값 |
| **Backbone** | 특징 추출부 | 이미지에서 유용한 특징을 뽑아내는 신경망 부분 |
| **Neck** | 중간 결합부 | 여러 단계의 특징을 결합해 검출 성능을 높임 |
| **Head** | 출력부 | 실제 객체의 클래스와 위치를 예측하는 부분 |
| **Epoch** | 학습 반복 횟수 | 전체 데이터를 한 번 학습하는 단위 |
| **Batch Size** | 묶음 크기 | 한 번에 학습하는 데이터 개수 |
| **LR (Learning Rate)** | 학습률 | 가중치를 업데이트하는 속도 |

---

## ⚙️ 3. YOLOv11 설치 및 실행 (기본 예시)

```bash
# YOLOv11 설치
pip install ultralytics

# 학습 (Training)
yolo detect train data=coco.yaml model=yolov11n.pt epochs=50 imgsz=640

# 추론 (Inference)
yolo detect predict model=yolov11n.pt source=example.jpg

# 평가 (Validation)
yolo detect val model=yolov11n.pt data=coco.yaml
