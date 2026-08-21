# Daily paper recommendations — 2026-08-19

- **연구 기준일(research date):** 2026-08-19
- **실제 검색 기간:** 2026-07-20 ~ 2026-08-19 (1일, 7일 검색에서 부합하는 논문이 부족하여 30일로 확대)
- **검색 쿼리:** `chest radiograph thoracic disease classification`

## 코호트 개요 (cohort-level only)

- 총 272건의 영상 레코드, 고유 환자 153명 (환자 단위 값 아님, 집계치)
- 성별: 남성 136 / 여성 136건 (레코드 기준)
- 연령 범위 9~87세, 평균 51.5세
- 촬영 자세: PA 184건, AP 88건
- 소견 라벨(`findings_label`) 분포: No Finding 145건(53%)이 가장 많고, 이어서 Infiltration 21건, Atelectasis 16건, Nodule 7건, Fibrosis 6건, Effusion 6건, Cardiomegaly 5건, Pneumothorax 5건 등 다양한 흉부 병변이 소수 사례로 분산. 여러 소견이 동시에 기록된 다중 라벨 조합(예: Effusion|Infiltration, Atelectasis|Effusion|Infiltration)도 다수 존재.

## 채택 논문

### 1. CLEAR: an auditable foundation model for radiology grounded in clinical concepts
(Nature Biomedical Engineering, 2026-07-22)

임상 개념 임베딩으로 흉부 X-ray를 해석 가능한 형태로 분류하는 파운데이션 모델. 미국·유럽·아시아 4개 외부 데이터셋에서 검증되어 최고 수준 분류 성능과 예측 근거 분해를 동시에 달성했다. 우리 코호트처럼 No Finding이 절반 이상이고 나머지가 저빈도 소견으로 흩어진 분포에서, 다기관 외부 검증이 된 모델의 참고 가치가 크다. 다만 우리 데이터에는 보고서 원문이나 개념 주석이 없어 CLEAR의 해석 가능성 자체를 재현할 수는 없다.

### 2. Grounding Radiology Report Findings into Medical Image Segmentation (CF2Seg)
(npj Digital Medicine, 2026-07-28)

방사선 보고서 문장을 지도 신호로 활용해 픽셀 단위 주석 없이 흉부 X-ray 병변을 분할하는 CF2Seg 프레임워크. 5만여 건 다기관 벤치마크에서 분포 변화와 주석 부족 상황에도 안정적 성능을 보였다. 우리 코호트는 `findings_label`에 다중 병변 조합 라벨은 있으나 픽셀 단위 주석이 없어, 보고서 라벨만으로 공간 정보를 추정하는 이 접근이 회고적 분석에 시사점을 준다. 다만 원문 보고서 문장이 없어 직접 검증은 불가하다.

### 3. Multicenter evaluation of four large language models for automated spine imaging diagnosis
(npj Digital Medicine, 2026-08-08)

3개 기관, 2만여 건의 실제 임상 보고서로 GPT-4o, Claude-4, Qwen-3 Max, DeepSeek-V3.1을 비교한 다기관 연구. 전반적 특이도·음성예측도는 높았으나 저빈도 질환에서 정밀도가 19~42%p 급락하는 롱테일 문제를 확인했다. 우리 코호트도 No Finding 대비 Nodule, Fibrosis, Pneumothorax 등 저빈도 소견이 다수라, 유사한 정밀도 저하가 흉부 X-ray 판독 보조에서도 나타날 가능성을 시사한다. 다만 이 논문은 척추 영상 보고서 대상 연구로 흉부 X-ray 영상 자체의 성능을 직접 알려주지는 않는다.

## 검토 및 배제 참고

동일 검색 창에서 함께 검토했으나 제외한 논문: UniMedDiff(영상 생성/증강 방법론, 환자 코호트 판독 readout 없음), Foundation models in biomedical imaging(관점 논평), Multimodal AI agents in healthcare(범위 검토), Review of open foundation models for ECG/PPG(비영상 파형 데이터), capsule endoscopy report generation(무관한 장기), Toward expert-level medical text validation(텍스트 검증 방법론), QoQ-Med3(범용 추론 모델, 임상 readout 미확인), A foundation model for acute abdomen diagnosis(CT 기반, 흉부 X-ray 코호트와 직접 연관성 낮음), 골다공증성 척추압박골절 자세영상 triage 논문(영상 양식이 posture/video로 상이).

## 참고 사항

**이 추천 목록은 자동 생성되었으며, 실제 임상 적용 전 반드시 담당 의사의 검토가 필요합니다.**
