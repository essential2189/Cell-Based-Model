# Anomaly Detection - Cell Based Model

- **작업 기간**
2021.10 ~ 2021.11 (2개월)

- **인력 구성(기여도)**
Preprocessing 1명 / AI modeling 2명 (100% / 70%), 총 2명

- **프로젝트 개요**
간 데이터를 이용해 암을 찾아내는 Unsupervised anomaly detection project (독성병리학).

자연어로 설명된 비정상에 관한 설명과 labeling된 비정상을 바탕으로, labeling되지 않은 모든 비정상을 포함한 비정상 후보를 detection한다. 현재 모든 데이터를 확인 해야하는 최종 결정자인 병리학자는 AI모델이 선정한 비정상 후보만을 보면 되게 된다 .

각 feature에 따른 모델을 분리하여 설계 후 essemble하는 방식으로 진행.

- **평가 방식**
제공받은 비정상 label과 labeling되지 않은 비정상 후보 모두 detection. 제공받은 비정상 label은 모두 detection 할 경우 recall 1로 간주. labeling되지 않은 비정상 후보를 줄이는 방식으로 precision 확보.

- **제한 사항**
    - 지도 학습 불가.
    - 클래스 불균형 (class imbalance).
    - 모든 label 제공 불가.
    - recall 1.
    - 빠른 inference 속도.
    - 데이터 공개 불가.

---

# 데이터 설명

- 총 데이터 개수 100개, 정상 90개, 비정상 10개.
- 데이터 형식 : Whole Slide Image (WSI), .mrxs 파일 ( + metadata, .dat 파일 )
- 데이터 크기 : 평균 (77000, 185000, 4), bitmap 기준 대략 56GB → 최적화 완료

- Label 설명
    - 데이터 이미지에서 비정상 영역에 xml 파일로 boundary 및 병명이 기제 되어 있다.
    - 한 비정상 데이터당 label 개수 : 2~5개, 20~30개 등으로 다양하다.
    - 각 feature 별 비정상 비율 : **세포핵(70%)** / 경계,비어있는 면적(20%) / 색상(10%)
    
    [Anomaly feature (데이터 상세)](https://www.notion.so/Anomaly-feature-dc37c24042b143acb45048d8676e97b3)
    

---

# 결과

[Process](https://www.notion.so/48bd2b6f7d244bbbb2a0640c14fc512c)

[Result](https://www.notion.so/0c249ff591404d0b93dda6144f6112e2)

---

# 문제점

- 고객 사 요구 사항 중 ‘recall 1’과 ‘supervised 불가’는 달성 했지만 ‘빠른 inference 속도’에 실패했다.
- 고객 사 요구 사항은 한 데이터 당 1분이다.

---

📁Github

[GitHub - essential2189/Cell-Based-Model](https://github.com/essential2189/Cell-Based-Model)

📄Reference

[HoVer-Net: Simultaneous Segmentation and Classification of Nuclei in Multi-Tissue Histology Images](https://arxiv.org/abs/1812.06499)