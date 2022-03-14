# emotion_thearpy

# files
추후 결정

## 22년 3월 3째주
|Todo|내용|수정 사항|
|--|--|--|
|1|action_data 수집 및 비교|X|
|2|emotion_data 튜닝|소스코드 수정 및 튜닝|
|3|recommendation 테스트|X|
|4|masking 기반 수치화 model 개발|X|

#### action data 수집 및 튜닝
1. action의 편차가 충분한가?
2. 구체적인 단어 대신에 wiki w2v에서 유사도가 높은 단어로 변경

#### emotion_data 튜닝
1. 현재 emotion_data(hand craft)에서 상위 N개의 평균을 사용하는데 수치가 1이 나옴 -> 소스코드 수정  
└ parsing이 단어 레벨이 아닌 글자 단위로 parsing이 되어 있었음 `split(" ")`을 추가해서 수정  
2. topn 파라미터 튜닝(상위 몇 개의 평균을 사용해서 사용해야 각 데이터의 분산이 크게 나오는가?  
└ 1 또는 2 사용 `두려움`, `슬픔`, `슬픔`에 대해서 데이터 추가 필요  
#### recommendation 테스트
1. 내부 flow 시각화 기능 추가
2. 시나리오 1. 감정을 입력 했을 때 활동을 추천 및 내부 flow 확인
3. 사나리오 2.색상 -> 감정 -> 효과 -> 활동 추천 및 내부 flow 확인
4. recommedation 방식 확인(효능이 유사한 상품 추천, 최대 차원이 비슷한 상품 추천, 보완하는 방식의 상품 추천)

#### masking 기반 수치화 모델 개발
현재 상태에서는 단어와 단어 사이의 유사도를 기반으로 사용함, 문장 레벨에서 동작 할 수 있게 masking을 적용해서 수치화 진행
