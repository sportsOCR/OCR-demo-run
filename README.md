# OCR-demo-run
Clovaai [deep-text-recognition-benchmark](https://github.com/clovaai/deep-text-recognition-benchmark)를 참고하여 프로젝트 진행
## About The Project
본 프로젝트는 한국 방송사의 스포츠 중계 화면에 특화된 OCR(Optical Character Recognition) 모델 개발을 목표로 하고 있습니다.
- 프로젝트 개요

OCR 기술은 이미지나 영상 속의 문자를 인식하는 기술로, 문자 영역 검출과 문자 인식, 크게 두 단계의 프로세스로 구성됩니다. 전통적인 OCR(문서의 글자 인식)과 달리, 동적이고 복잡한 배경의 문자 인식 정확도 저하가 주요 문제점으로 대두되고 있습니다. 이러한 문제를 해결하기 위해, 영역 속의 글자를 인식하는 데 특화된 STR(Scene Text Recognition) 모델을 활용하였습니다.

- 모델 선정

OCR 모델 구조는 네이버 Clova AI가 제안한 STR 모델 중 가장 우수한 성능을 보여준 TPS-ResNet-BiLSTM-Attn 구조를 기반으로 하였습니다. 이 구조는 TPS(Thin Plate Spline) 기반의 변환, ResNet 기반의 특징 추출, BiLSTM 기반의 시퀀스 모델링, Attention 기반의 예측을 결합한 형태로, 복잡하거나 변형된 텍스트를 정확하게 인식하는 데 뛰어난 성능을 보여줍니다. 또한, `스포츠 중계 영상 내 문자 인식 모델의 성능 분석 연구 `논문의 실험을 통해 한국어 인식에 효과적임을 입증했습니다.

- 데이터셋 및 학습

기존에 영어 데이터셋(MJ, ST)으로 학습된 모델을 한국어 글자체 데이터셋을 활용하여 새롭게 학습하였습니다. 이를 통해 한글 텍스트에 대한 인식 능력을 향상 시키고, 스포츠 중계 화면에서 한글 정보를 더욱 정확하게 인식할 수 있습니다.

## Project Files Description
  1. `FrameExtractor.py`
     - input video에서 300frame단위로 이미지 추출
     - 이미지 추출할 때마다 recognition 진행
  2. `cropping.py`
     - input coordinates 적힌 좌표대로 이미지 crop후 지정한 폴더에 저장 
  3. `base.py`
     - base 인식
  4. `postprocess.py`
     - recognition 오류 글자를 후처리를 통해 올바르게 수정
     - 코사인 유사도, 자카드 유사도 사용
  5. `ocr_recognition.py`
     - model을 load하여 ocr recognition 진행
  6. `ocr_main`
     - 실행 파일
## Run
- input
  - `channel`: 방송사 명
  - `input_video`: 입력 경기 video 주소
  - `input_coords`: 해당 비디오의 (팀명1, 팀명2, 점수1, 점수2, 투수명)의 좌표값이 적힌 txt파일 주소
  - `input_folder_postprocess`: 팀명, 숫자, 해당 경기에 참가하는 선수명 txt파일이 있는 폴더 주소
```
python ocr_main.py --channel mbc --input_video videos/mbc0604.mp4  \
--input_coords input_folder/text/mbc.txt --input_folder_postprocess input_folder/words/ \
--saved_model saved_models/TRBA_33211/best_accuracy.pth
```

## Result
- output
  - [log_demo_score.txt](log_demo_score.txt)
  - [scoretojson.json](scoretojson.json)
![image](https://github.com/sportsOCR/OCR-demo-run/assets/73013625/e7c47293-da11-4e6d-8a6f-6559a39ce401)
