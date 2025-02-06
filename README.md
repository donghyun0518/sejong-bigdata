<h1 style="text-align: center;">🚲 제 5회 세종특별자치시 빅데이터 분석 아이디어 공모전</h1>
<hr>
<p style="text-align: center;">
    <a href="https://github.com/donghyun0518/sejong-bigdata-mclp-optics/blob/main/%EC%84%B8%EC%A2%85%EC%8B%9C%20%EA%B3%B5%EB%AA%A8%EC%A0%84%20%EC%B5%9C%EC%A2%85.pdf" target="_blank">
        <img src="https://github.com/donghyun0518/sejong-bigdata-mclp-optics/blob/main/%EC%84%B8%EC%A2%85%EC%8B%9C%ED%91%9C%EC%A7%80.png" alt="Project Cover" style="width: 1000px; border: 1px solid #c9d1d9; border-radius: 8px;">
    </a>
</p>

## 🔍 프로젝트 개요
- **목적** : 세종시 출퇴근 시간대 교통 체증 완화를 통한 시민의 삶의 질 향상
- **주제** : 세종시 공공 전기자전거 도입을 위한 거치대 최적 입지 선정
- **기간** : 2024.08.09 ~ 2024.09.30 (약 7주간)
- **팀 구성** : 4인
- **성과** : 본선 진출

## ⚙️ 주요 수행 과정
**1. **문제 정의****
   - 출퇴근 시간대 도로 정체로 인한 시민들의 불편함 존재.
   - 도로 정체로 인한 운전자들의 스트레스 증가.
   - 공공자전거(어울링)의 도입으로도 도로 정체가 해결되지 않고 있는 것을 확인함.
   - 기존 공유전기자전거(일레클)의 이용률이 증가하는 것을 확인하였고, 이 공유전기자전거의 이용, 관리 및 주차 문제가 있다는 시민의 불편함을 확인하여 이를 개선하고자 분석을 진행.

**2. **데이터 수집 및 전처리****
   - 데이터 출처 : 공공데이터 포털, 세종시 교통 빅데이터분석 시스템, KOSIS 국가통계포털
   - 전처리 작업
     - 이미지 크기 통일화
     - 라벨링 json 파일에서 사용할 라벨링 형식(바운딩 박스) 추출

**3. **모델 설계****
   - 모델 선정 : YOLOv8m 기반의 실시간 객체 탐지 모델 활용
   - 모델 학습:
     - 데이터셋을 훈련, 검증, 테스트 데이터로 분할
     - 크로스엔트로피 손실 함수와 Adam 옵티마이저를 사용해 학습진행.
     - CUDA를 활용하여 모델 학습진행.
   - 평가 지표 :
     - 정확도(Precision), 재현율(Recall), F1 Score 및 mAP50(Mean Average Precision)으로 성능 평가.

**4. 모델 테스트 및 결과 분석**
   - 테스트 데이터셋을 통해 모델의 병변 탐지 정확도 확인.
   - 위/대장 두 장기를 동시에 학습시킬 시 현재 부위가 위인지 대장인지 구분하지 못하는 문제 발견
     - 해결 방법 :
       - 위와 대장을 따로 학습시켜 인터페이스 구현 시 선택 가능하도록 설계
   - 정확도 확인 결과 :
     - 대장
       - Precision : 0.74 , Recall : 0.699, mAP50 : 0.72
     - 위
       - Precision : 0.75 , Recall : 0.63, mAP50 : 0.69

**5. 인터페이스 및 홈페이지 구현**<br>
    [![유튜브에서 시연 영상보기](https://github.com/donghyun0518/final-project-endoscope/blob/main/%EB%82%B4%EC%8B%9C%EA%B2%BD%EC%8B%9C%EC%97%B0%EC%98%81%EC%83%81%ED%91%9C%EC%A7%80.png)](https://www.youtube.com/watch?v=94uCWk3kKMI)
   
**6. 한계점**
   - 병변의 종류가 적어 다양한 병변 탐지 불가능
   - 개인 컴퓨터의 성능 제한으로 인해 더 큰 YOLO 모델에 적용하지 못함.

## 🧑🏻‍💻환경
- Python
- VScode
- CUDA

