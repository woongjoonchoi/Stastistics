# 데이터분석

## 데이터 : Amazon 2009~ 2019 Top 50 Amazon Best Selling 

### 선택이유 : 
Kaggle에서 데이터셋을 찾아보는데  범주형 자료와 , 수치형 자료의 columun을 갖고있는 데이터중 이것이 눈에 띄어서 선택하게 되었다.
그리고, 평소에 구매 데이터로 분석을 하고 싶었는데, 이번에 기회가 되어서 분석하기로 결정한 이유도 있다.

### 기술통계분석:

![image](https://user-images.githubusercontent.com/50165842/113001691-050be480-91ac-11eb-9605-bb9684891f31.png)   
![image](https://user-images.githubusercontent.com/50165842/113001729-0dfcb600-91ac-11eb-8245-c777291569fa.png)   
![image](https://user-images.githubusercontent.com/50165842/113001748-135a0080-91ac-11eb-8fa0-2e786dba9e01.png)

User Rating의 평균은 4.63이고  , 중앙값은 4.70 이다.
Reviews는 평균은 12022 이고, 중앙값은 8500이다.
Reviews의 Range는 87433 이고  ,UserRating의 Range는 1.63이다.
Variance는 Reviews가 1.40e+8 이고 , User Rating은 0.44정도이다.
Reviews의 Data가 User Rating에 비해 좀더 퍼져 있다는 것을 알 수 있다.
User Rating은 skewness가 음수이고, Reviews는 양수이다.
User Rating은 오른쪽에 값들이 치우쳐져 있고 , Reviews는 왼쪽에 치우쳐져 있다는 것이다.
Kurtosis는 User Rating이 4.54 , Reviews가 9.15이다 .
Reviews가 좀더 분포가 좀 더 뾰족한 형태의 분포이다.


### T-test:
![image](https://user-images.githubusercontent.com/50165842/113001867-308ecf00-91ac-11eb-911f-0f2f4f4b7d56.png)

Shapiro-Wilk 로 정규성 검정을 해보았는데 , p값이 0.05보다 작으므로 , 정규분포를 따르지 않습니다.

Non_fiction,Fiction으로  나누고, 특정기간에 대한 User_Rating,Reviews에 대하여 비모수 T-Test를 (Mann-Whiteny U)하겠습니다.

#### User Rating Descriptive

![image](https://user-images.githubusercontent.com/50165842/113001988-54eaab80-91ac-11eb-87d7-c3692e53aa0a.png)

![image](https://user-images.githubusercontent.com/50165842/113002058-65028b00-91ac-11eb-8bbe-a63f3bb9f0da.png)   

![image](https://user-images.githubusercontent.com/50165842/113002099-6c299900-91ac-11eb-8b3d-103a5a4ce758.png)

통계학적으로 어떤지 확인 해보겠습니다.
User_Rating,Reviews에서 Non-Fiction,Fiction의 Rank를 보겠습니다.
이를 통해, 두 집단의 중앙값이 같은지 다른지를 검증하겠습니다.

![image](https://user-images.githubusercontent.com/50165842/113002178-7fd4ff80-91ac-11eb-99dc-aea6b88d6c8e.png)

유의수준을 0.05로 지정햇을 때 , p-value값이 userrating,reviews 모두 0.05보다 작게 나오므로, Fiction,Non-Fiction에 관계없이 같다라는 가설을 부정해야 합니다.

매 해의 Amazon BestSeller의 리뷰수,유저 평점은 Fiction,Non_fiction 장르별로 구분하면 달라집니다.
즉, 아마존 유저들의 Fiction,Non Fiction에 대한 리뷰수는 구매율로 볼 수 있으며 , Fiction,Non_fiction에 대한 구매율 다름을 알수 있습니다. 아마존 유저들은 Fiction쪽 구매가 많음을 알 수 있습니다.
아마존 유저들의 Fiction에 대한 평가가 Non-fiction에 대한 평가보다 좋음을 알 수 있습니다.

### ANOVA TEST

Price가 10보다 작으면 1, 10이상 20미만이면 2, 20 이상이면 3 으로 그룹핑 했습니다.
그다음에 이 Price에  대하여 Anova Test를 하였습니다. 

![image](https://user-images.githubusercontent.com/50165842/113002366-a98e2680-91ac-11eb-8b43-3e6440006319.png)

정규성 검정에서 이와 같이 p값이 0.05보다 작게 나왔기 때문에  정규분포를 따르지 않는다고 봐야하기 때문에
비모수 anova Test를 진행하기로했습니다. 

![image](https://user-images.githubusercontent.com/50165842/113002421-b874d900-91ac-11eb-9bfe-b7b5c239af30.png)

![image](https://user-images.githubusercontent.com/50165842/113002484-c6c2f500-91ac-11eb-859f-032e133dece0.png)

![image](https://user-images.githubusercontent.com/50165842/113002502-cb87a900-91ac-11eb-8261-ff1ddad6f01b.png)

![image](https://user-images.githubusercontent.com/50165842/113002521-d2162080-91ac-11eb-978f-0a73566c1edc.png)

이러한 결과가 나왔고, Reviews의 경우 1,2번 Price가 p값이 0.05보 크고 , User Rating은 2,3번  집단에서 p값이 더 크게 나왔습니다.

따라서, 리뷰갯수는 Price가 10이하인 책과 10초과 20 미만인 책의 Median이 같고 , 
평점은 Price가 20이상 30미만인 책과 30이상인 책들이 Median이 같다 볼 수 있습니다.
즉, 아마존 유저들은 Price가 20이상인 책들에 대하여 비슷한 평가를 내렸고, 10 미만인 책들에 대하여 Price가 20이상인 책들에 비해 살짝 더 좋은 평가를 내렸습니다.   Price가 30이상인 책들을 잘 구매하지 않으며, 0 ~ 10인 책과 , 10 ~ 20의 가격의 책들의 구매량이 비슷합니다.


### 카이제곱 검정

Reviews를 만단위로 쪼개서, Nominal로 바꾼다음에 카이제곱 검정을 실시 하였습니다.

![image](https://user-images.githubusercontent.com/50165842/113002721-07bb0980-91ad-11eb-9568-7e75eef5dc6c.png)

이 때,p_value가 유의수준인 0.05 보다 작은 0.01 이나왔습니다. 이는 가격 과 리뷰수가 서로 종속적이다 라 볼 수 있습니다. 리뷰수를 구매량으로 치환해서 생각을 하게 되면 , 이는 구매량과 가격이 연관이 있다고 볼 수 있게 되는 것입니다.
앞서 얻은 결론과 연관지으면, 책이 쌀수록 구매량이 더 높다 볼수 있게 됩니다. 

### Regression

![image](https://user-images.githubusercontent.com/50165842/113002790-1a354300-91ad-11eb-89bf-8d3f1582f905.png)

User-Rating과 ,Reviews에 대해 Linear Regression으로 회귀 분석을 하였습니다.

p값이 0.05보다 크기 때문에 Reviews와 User Rating은 직선상의 관계에 있다고 볼 수 없습니다.

즉 , 리뷰개수와 User_rating은 관련이 없다는 뜻입니다.

![image](https://user-images.githubusercontent.com/50165842/113002861-2caf7c80-91ad-11eb-81bf-ea5728f6e060.png)

가격과 평점의 관계를 직선 모델 관계인지 검증해보았다.
p값이 0.003이므로 0.05 보다 작기 때문에 직선상의 관계에 있다고 볼수 있습니다.
즉, 가격이 비싼 책일수록 높은 평점을 받았다고 볼 수 있습니다.


### 결론:
#### 1.	아마존 유저들은 Fiction의 구매갯수가 Non-Fiction의 구매갯수 보다 많다.
#### 2.	아마존 유저들은 Fiction 책을 Non-Fiction보다 고평가 해준다.
#### 3.	아마존 유저들은 가격이 비싼 책보다 싼책을 더 많이 구매한다.
#### 4.	아마존에서 가격이 비싼 책일수록 평점이 더 높게 받는다.
#### 5.	리뷰수와 평점은 관련이 없다.

