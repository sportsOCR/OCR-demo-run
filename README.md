# OCR-demo-run

## About The Project

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
