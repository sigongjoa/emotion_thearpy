# 감정 데이터 Test
현재 감정 키워드와 차원 유사어 사이의 관계에 대해서 상위 N개의 평균을 추정치로 사용
이때 상위 몇 개로 하는 것이 좋은가?

## 감정 키워드
| 감정 | 효능 |
|:---|:---|
| 행복 | 향유 낙관적 느낌 생각 즐기 |
| 우울 | 행동 도움 생활 치료 명상 |
| 슬픔 | 사랑 도움 가족 시간 활동 |
| 열정 | 상기 집중 노력 몰입 휴식 |
| 분노 | 정지 회피 긍정 마음 호흡 |
| 두려움 | 직면 변화 대화 집중 용기 |

## 차원의 유사어 확인
| 효과 | 유사어 |
|---|---|
| 기운(에너지) | 정열 활기 기력 생기 활발 |
| 회복 | 낫(다) 치료 휴식 극복 재활 |
| 순환 | 운반 유지 조절 공급 생명 |
| 정화 | 진정 맑(다) 없애(다) 깨끗하 |

└ 동사의 경우에 w2v 모델에 없어서 다음과 같이 어미를 분리해줌


## 추정 방법


## 비교
현재 감정 키워드는 감정을 고양(또는 극복) 하는 내용을 키워드로 사용
상위 N개로 추정치를 확인
위의 topn 파일에 결과치를 저장함


|topn|비교|code|
|--|--|--|
|1|이상치의 영향을 많이 받음|--|
|3|later|--|
|5|평균 효과나 나타난 상위 25와 비교 했을 때 거의 유사한 패턴을 보이면서 슬픔을 극복하려면 `에너지`가 더 필요하다고 생각되는 상위 5개의 평균으로 했을 때 이를 잘 나타냄|--|
|7|later|--|
|25|평균 효과 확인|--|

