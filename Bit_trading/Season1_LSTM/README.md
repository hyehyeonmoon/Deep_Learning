# Bit-trading Dayon season1 
- BI-LSTM을 사용해서 40분을 기반으로 다음 1분 예측하는 task를 통해 120분의 주가 예측
- 실행환경은 colab python이며 cpu 사용
- gpu 사용, slope 만드는 것, min-max scaling(표준화) 처리가 남아있음


# Season1 제출(1차) 
## 파일
|File|Description|
|:-- |:-- |
|Season1_final_submission_train.ipynb|BILSTM을 사용하여 40분 간격으로 다음 1분을 에측하는 task 수행|
|Season1_final_submission_prediction.ipynb|학습한 파라미터들을 이용해 test set의 120분 예측하고 submission file 만들기|
|100n_1L_BILSTM_7ep_5feature.pth|100개의 sample과 5개의 feature를 가진 데이터에 대해서 각각 7epoch씩 업데이트를 시킨 결과 파라미터|

## 작동원리
- (batch_size, time_length, n_feature)를 BILSTM model에 입력하면 40분 간격으로 다음 1분(batch_size, 1, n_feature)을 예측하게끔 만듦
- 입력의 결과값이 나오면 그것을 다시 입력값으로 사용하는 식으로 다음 120분을 예측
- open, high, close, low, coin_index 5개의 feature를 이용
- 100개의 sample_id 하나씩 총 7번 파라미터들을 업데이트 하며 얻은 파라미터를 이용해 test 값 예측 => public score : 10022.3825

# Season1 제출(2차)
|Date|Description|
|:-- |:-- |
|utils| 데이터 불러오기 및 모델 형태에 맞게 변환 |
|rnn.py | BILSTM을 사용하여 40분 간격으로 다음 1분을 예측하는 모델|
|trainer.py| 1epoch train 이후 validate에서 loss를 계산해서 best model을 저장하는 일련의 과정|
|train.ipynb | utils, rnn, trainer 모두 합쳐놓은 실행파일 |

## 작동원리
- 한 개의 sample에 대해서 여러 번의 업데이트를 하는 것이 아닌 약 7000개의 sample에 대해서 한 번씩만 업데이트를 한 뒤, 총 n번의 epoch을 돌리는 것
- mini batch를 이용하면 좋지만, split_data와 40분 간격이라는 두 점 때문에 하지 못함
