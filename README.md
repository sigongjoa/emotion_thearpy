# emotion_thearpy

# files

## check_emtion_data.ipynb
> https://github.com/sigongjoa/emotion_thearpy/blob/main/check_emtion_data.ipynb  
데이터 확인 및 각 감정에 대해서 merge 진행  
heatmap을 통해서 각 명사들 간의 유사도를 확인(wiki 모델)

## count&sims.csv
[감정 , 감정 count, 감정 sims]  
감정 : 현재 감정에 대해서 therapy 데이터 안에 나온 단어들  
감정 count : 위 단어들에 대한 빈도수  
감정 sims : 단어에 대해서 wiki 모델에 대한 유사도  


## data.csv
therapy 데이터에 대해서 각 감정별로 다 연결  

## data.xlsx  
text 형태의 therapy 데이터

## result_original.xlsx
therapy 데이터에서 나온 단어와 그 단어가 나온 빈도수 

## sim_based_mapping_wiki.ipynb
기존의 wiki를 이용한 유사도 추정 방법(유사어는 이전의 단어 그대로 사용)

## simwords 1000 in wiki data.csv
각 감정들에 대해서 유사도가 높은 상위 1000개의 단어들 과 이에 해당하는 유사도 

## 유사어 확인.ipynb
각 감정 별로 유사도가 0.3 이상인 단어들을 
