## Bit-trading Season2


| File | Description| Reference|
|:-- |:-- |:-- |
|ARIMA_Prophet| Arima와 Prophet으로 적합하여 결과값을 max한 것(Season1 우승작 Clone coding)| [Link](https://dacon.io/competitions/official/235740/codeshare/2473?page=1&dtype=recent)|
|pytorch_forecasting_example|Pytorch Lightning에서 제공하는 TFT 예제 실습|[Link](https://www.notion.so/Pytorch-forecasting-085c929c54184a6a9e3c324e60df97b5#cc19dbcfd3f640729edd815a4c57bee9)|
|TFT_basic| Temporal Fusion Transformers를 이용하여 120분을 예측|. |
|TFT_changing_variable| basic에서 feature importance를 통해 변수를 줄이고 다시 적합|. |
|TFT_changing_time| 수렴되는 것을 막기 위해 60분을 예측 |. |
|N-BEAT| M4 Competition에서 우승한 신경망 구조의 시계열 예측 모델을 사용해 봄|. |
|Season2_Final_submission| array_to_submission조건 추가 및 ARIMA, Prophet, TFT, N-Beat 결과들을 모두 max를 통해 하나로 합침 |. |


## 후기

Public Score : 46th  
Private Score : 40th

신경망 구조를 가진 딥러닝 모델들은 모두 수렴하는 형태를 보였다. 이에 비해 ARIMA와 Prophet은 정확하지 않지만 적어도 수렴하지는 않았다.  
"주식은 예측할 수 없다"는 것을 통계적으로 증명됬음에도 암호화폐 120분을 10개도 안 되는 변수를 가지고 예측한다는 것은 불가능에 가까운 일로 보인다.  

신경망 구조의 시계열 모델들에 대해 알아볼 수 있어서 재미있었고, 다음번에는 [CNN-LSTM model](https://www.notion.so/LSTM-6fb4ba69f08e4839925178879a4a5d5a#59c6fdb15a5247fca7529c16268984bb)과 [Informer model](https://paperswithcode.com/task/time-series-forecasting)을 사용하여 예측을 도전해 보고 싶다.

## 실행 환경

Google Colab에서 사용
[Data](https://dacon.io/competitions/official/235740/overview/description) : Daycon-인공지능 비트 트레이더 경진대회 시즌 2

## 코드 오류 및 개선점

| File | Description| Reference|
|:-- |:-- |:-- |
|ARIMA_Prophet| Valid set이 없어 검증할 수 없으며 Train set에서는 수렴하지 않는 sample들이 있어 모수를 맞춰주기 힘듦, auto arima는 적절한 모수를 찾아주지 못하는 것을 다른 notebook들을 통해 알 수 있음| [Link](https://dacon.io/competitions/official/235740/codeshare/2473?page=1&dtype=recent)|
|pytorch_forecasting_example|.|[Link](https://www.notion.so/Pytorch-forecasting-085c929c54184a6a9e3c324e60df97b5#cc19dbcfd3f640729edd815a4c57bee9)|
|TFT_basic| Temporal Fusion Transformers에서 model에 sample_id 변수를 known으로 잘못 입력함|. |
|TFT_changing_variable| basic에서의 오류를 수정하였지만 120분 동안 비트코인 가격이 수렴하는 형태를 보임|. |
|TFT_changing_time| 수렴되는 것을 막기 위해 60분을 예측했음에도 여전히 수렴함 |. |
|N-BEAT| 수렴되는 양상이 보이고 메모리의 한계로 인해 4epoch까지만 학습|. |
|Season2_Final_submission| max 이외의 metric을 통해 데이터를 합친다면 더 좋은 결과를 기대해 볼 수 있을 것 같음 |. |





