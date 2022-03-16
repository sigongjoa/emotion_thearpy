# emotion_thearpy

# files
추후 결정

## 22년 3월 3째주
|Todo|내용|수정 사항|
|--|--|--|
|1|action_data 수집 및 비교|X|
|2|emotion_data 튜닝|소스코드 수정 및 감정 데이터 추가, scaling 추가|
|3|recommendation 테스트|감정과 행동의 수치화를 MAE기반으로 유사도를 측정후 추천|
|4|masking 기반 수치화 model 개발|X|

#### action data 수집 및 튜닝
1. action의 편차가 충분한가?
2. 구체적인 단어 대신에 wiki w2v에서 유사도가 높은 단어로 변경

#### emotion_data 튜닝
1. 현재 emotion_data(hand craft)에서 상위 N개의 평균을 사용하는데 수치가 1이 나옴 -> 소스코드 수정  
└ parsing이 단어 레벨이 아닌 글자 단위로 parsing이 되어 있었음 `split(" ")`을 추가해서 수정  
2. topn 파라미터 튜닝(상위 몇 개의 평균을 사용해서 사용해야 각 데이터의 분산이 크게 나오는가?  
└ 상위 1개 또는 2개 사용 `두려움`, `슬픔`, `슬픔`에 대해서 데이터 추가 필요   
└─ item과 감정에 대해서 w2v으로 가장 유사한 단어를 표시 : https://github.com/sigongjoa/emotion_thearpy/blob/main/notebooks/emotion_data_tuning.ipynb   
└── 단어를 바꾼다고 해도 그렇게 큰 차이는 없을 것 같음 -> Scaling 진행 : 유사도를 2배로 함(유사도 = wiki 유사도 * 2)
3. Scaling  
└ wiki 모델 각 단어와 가장 유사한 단어에 대해서 유사도가 0.5 ~ 0.7 사이임, Scaling을 적용(wiki의유사도 * 2를 유사도로 적용)  
└─ 이전의 방식보다 조금은 더 분별을 잘 하고 있음  
└─ Scaling 전의 recommendation :  https://github.com/sigongjoa/emotion_thearpy/blob/main/notebooks/recommendation.ipynb  
└─ Scaling 이후의 recommendation :  https://github.com/sigongjoa/emotion_thearpy/blob/b037e0c7535474c1dcb504d281abd421dabd8e01/notebooks/recommendation.ipynb  
#### recommendation 테스트
1. 내부 flow 시각화 기능 추가  
2. 시나리오 1. 감정을 입력 했을 때 활동을 추천 및 내부 flow 확인  
└ MAE로 유사도를 계산을 했을 때 부정확한 값이 존재함  
└─ since : 감정과 item에 대해서 수치화가 제대로 되지 않음  
└─ since : 둘 사이의 유사도를 계산하는 방식을 다른 방식(MAE, 피어슨 유사도, 코사인 유사도, 상위 N개의 높은 값 사용)  
└── 수정 결과 : 그렇게 큰 차이점을 보이지는 않음(MAE방식과 가장 유사한 item을 추천하는 방식이 제일 좋은 성능을 보임)  
3. 사나리오 2.색상 -> 감정 -> 효과 -> 활동 추천 및 내부 flow 확인  
 └ 감정에 대해서 각 item에 대해서 유사도를 시각화 이후에 가장 유사도가 높은 제품을 추천  
4. recommedation 방식 확인(효능이 유사한 상품 추천, 최대 차원이 비슷한 상품 추천, 보완하는 방식의 상품 추천)  

#### masking 기반 수치화 모델 개발
현재 상태에서는 단어와 단어 사이의 유사도를 기반으로 사용함, 문장 레벨에서 동작 할 수 있게 masking을 적용해서 수치화 진행
