# 도치약국

## CodingHedgehog (코딩하는 고슴도치)

### 팀원 
__안현진,배선영,이상현,양소영__

### 기술 스택
<p>
    <img src="https://img.shields.io/badge/JAVA-007396?style=flat-square&logo=java&logoColor=white">
    <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white">
    <img src="https://img.shields.io/badge/Android Studio-3DDC84?style=flat-square&logo=android&logoColor=white">
    <img src="https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=Node.js&logoColor=white">
    <img src="https://img.shields.io/badge/Tensorflow-FF6F00?style=flat-square&logo=Tensorflow&logoColor=white">
    <img src="https://img.shields.io/badge/mysql-4479A1?style=flat-square&logo=mysql&logoColor=white">
    <br>
    <img src="https://img.shields.io/badge/amazon aws-232F3E?style=flat-square&logo=amazonaws&logoColor=white">
    <img src="https://img.shields.io/badge/google cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white">
    <img src="https://img.shields.io/badge/linux-FCC624?style=flat-square&logo=linux&logoColor=white">
</p>

#### 문서 관리 : <img src="https://img.shields.io/badge/slack-4A154B?style=flat-square&logo=slack&logoColor=white">
#### 일정 관리 : <img src="https://img.shields.io/badge/trello-0052CC?style=flat-square&logo=trello&logoColor=white">
<hr>

### 화면 이미지

<div align="center">
    <img src="https://user-images.githubusercontent.com/46213180/122176760-ecb08980-cebf-11eb-9b81-76eaa7297045.png" width="25%" height="80%">
    <img src="https://user-images.githubusercontent.com/46213180/122176882-0b168500-cec0-11eb-834e-7819078d145c.png" width="25%" height="80%">
    <img src="https://user-images.githubusercontent.com/46213180/122176926-15d11a00-cec0-11eb-92c8-6a82b9145bf8.png" width="25%" height="80%">
</div>

2. 텍스트 검색<br>
<img src="https://user-images.githubusercontent.com/46213180/122176882-0b168500-cec0-11eb-834e-7819078d145c.png" height="500"><br>
3. 이미지 검색<br>
<img src="https://user-images.githubusercontent.com/46213180/122176926-15d11a00-cec0-11eb-92c8-6a82b9145bf8.png" height="500"><br>
4. 검색 결과 목록<br>
<img src="https://user-images.githubusercontent.com/46213180/122176961-1d90be80-cec0-11eb-919f-108090252af2.png" height="500"><br>
5. 알약 상세 정보<br>
<img src="https://user-images.githubusercontent.com/46213180/122176992-271a2680-cec0-11eb-8999-888cf2181813.png" height="500"><br>
6. 즐겨찾기 목록<br>
<img src="https://user-images.githubusercontent.com/46213180/122177029-2e413480-cec0-11eb-9f02-91ce88fed643.png" height="500"><br>
7. 알약 간 상호작용 목록<br>
<img src="https://user-images.githubusercontent.com/46213180/122177076-3d27e700-cec0-11eb-986d-477d89b07a85.png" height="500"><br>
8. 복용알림 기능<br>
<img src="https://user-images.githubusercontent.com/46213180/122177120-46b14f00-cec0-11eb-8c80-3f94527b05f5.png" height="500"><br>
9. 건강관련 카드뉴스<br>
<img src="https://user-images.githubusercontent.com/46213180/122177159-4fa22080-cec0-11eb-9920-3d7cc52900eb.png" height="500"><br>

<br>

## 데이터
----------------------------
### 1. 데이터 수집
- 기본 데이터
  - 공공 API를 통해 데이터 수집
  - public_api 폴더의 코드 사용
- 테스트 데이터
  - public_api/download_test.py 참고
- 상세 데이터
  - 약의 효능,복용방법에 대한 데이터 수집

### 2. 데이터 라벨링
- 딥러닝
  - api 데이터에서 내용 탐색 후 자동 라벨링
- 객체 탐지
  - object 영역 labelImg 도구로 라벨링
  - [labelImg](https://github.com/tzutalin/labelImg)

### 3. 이미지 편집
1. 객체 탐지를 통해 알약 객체 찾기
2. 객체 영역의 좌표값 저장
3. openCV를 통해 해당 좌표값을 기준으로 사진 자르기

<br>

## 딥러닝
----------------------------
### 0. 이미지 전처리
1. OpenCV의 Bilateral Filter를 기반으로 이미지 화질을 개선함.
2. 알약 이미지에서 Canny Edge 알고리즘과 LAB 색상 공간, Adaptive Threadhold를 적용해  그림자를 제거함.

### 1. 모양 학습
- 알약 이미지에 대해 Zernike Moment를 이용하여 알약의 모양을 추출함.

### 2. 색상 학습
- 알약이 탐지된 이미지에서 OpenCV를 활용한 색상 평균 추출

### 3. 문자 학습
- 알약 이미지에 대해 OpenCV를 활용해 윤곽(Contour)을 추출하고 CNN Deep Learning 모델로 학습 및 OCR을 이용하여 알약의 글자를 추출함

### 4. 객체 탐지
1. 학습
    - [Darkflow](https://junyoung-jamong.github.io/deep/learning/2019/01/22/Darkflow%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%B4-YOLO%EB%AA%A8%EB%8D%B8-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EB%94%94%ED%85%8D%EC%85%98-%EA%B5%AC%ED%98%84-in-windows.html)
    - predefined_classes.txt,labels.txt 내용 Pill로 변경
    - tiny-yolo.cfg 내용 중 filters=(5+classes)*5=30/classes=1로 변경
    - data 디렉토리 아래에 annotations,dataset 디렉토리를 생성하고 라벨링된 데이터를 넣어줌
    - 명령어를 통해 학습시켜주고 TensorBoard를 통해 loss의 수렴정도를 확인함
2. detection
    - [Object Detection](https://junyoung-jamong.github.io/machine/learning/2019/01/25/Android%EC%97%90%EC%84%9C-%EB%82%B4-YOLO%EB%AA%A8%EB%8D%B8-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0.html)
    - 학습 데이터의 *.pb파일를 assets에 추가해줌
    - DetectorActivity.java에서 파일 경로와 DetectorMode를 변경
    - TensorFlowYoloDetector.java에서 클래스 개수와 label명을 변경
3. 성능평가
    - testdata에 대한 이진분류결과표를 작성
    - sklearn 라이브러리를 이용하여 학습모델에 대한 평가점수(정확도, 정밀도, 재현율, f점수)를 계산한다.
    
<br>    
    
## 웹서버
----------------------------
### 1. DB 설계
### 2. DB 구축
### 3. 서버 구축
- nodejs 웹 서버 구축
### 4. 서버 통신
- express 모듈을 활용한 안드로이드 앱과의 통신
- sequelize 모듈을 활용한 mysql 데이터베이스 통신
- multer 모듈을 활용 안드로이드 앱으로부터 서버로 사진 전송

<br>

## 애플리케이션
----------------------------
### 1. UI 제작
- Material UI 사용
- PowerMockUp으로 스토리보드 작성

### 2. 기본기능 제작
- 객체 탐지 카메라 기능
- 기본 정보 제공
- 복약 알림 : 복용횟수에 따라 알림 발생
- 즐겨찾기 : 자주 검색하는 알약을 즐겨찾기에 저장가능

### 3. 웹서버 통신
- 기본 검색 기능(텍스트로) : 알약이름,식별표시,색상,모양 을 선택하면 해당하는 알약리스트를 반환

### 4. 사진 검색 기능
- 사용자가 카메라 화면에 알약을 배치하면 TTS(Text-to-Speech)를 통해 알림 [객체탐지]
- 촬영 버튼 클릭 시, 해당 알약의 이미지와 좌표를 서버에 전송
- 서버에서 이미지 전처리 후 알약의 색상, 모양, 글자를 인식하여 해당하는 알약 리스트를 반환
