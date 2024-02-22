# OCR-demo-run

## About The Project

## Project Files Description

## Run
- input
  - `channel`: 방송사 명
  - `input_video`: 입력 경기 video 주소
  - `input_coords`: 해당 비디오의 (팀명1, 팀명2, 점수1, 점수2, 투수명)의 좌표값이 적힌 txt파일 주소
  - `input_folder_postprocess`: 팀명, 숫자, 해당 경기에 참가하는 선수명 txt파일이 있는 폴더 주소
```
python ocr_main.py --channel mbc --input_video videos/mbc0604.mp4  \
--input_coords input_folder/text/mbc.txt --input_folder_postprocess input_folder/words/ 
```

## Result
