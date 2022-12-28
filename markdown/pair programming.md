# Python - Data 수집 프로젝트



## 준비사항 

### 사용 API

-  TMDB API(https://developers.themoviedb.org/3) 

### 개발언어/프로그램 

- Python 3.9 이상 
- 아래중 택1
  - VS code
  - Jupyter notebook

### 필수 라이브러리 

- `requests ` 

  ```sh
  $ pip install requests
  ```



### `requests` 사용법

```python
import requests  # requests 모듈 호출

res = requests.get(URL)  # URL 로 요청 보냄

data = res.json()  # 요청의 응답 JSON을 *dict*로 변환함

print(data)  # data 확인(list or dict일 확률이 높음)
```





## 문제

### Problem A

인기 영화 조회 인기 영화의 개수를 출력합니다. 

1. `requests`를 이용하여 인기 영화 정보(Get Popular)에 요청을 보냅니다. 

import requests

key = '68c36bcac7f38b09c933975c8ce9c200'
url = 'https://api.themoviedb.org/3/movie/popular?api_key=68c36bcac7f38b09c933975c8ce9c200&language=en-US&page=1'

data = requests.get(url).json()

print(data)

1. popular를 기준으로 받아온 데이터에서 영화 리스트의 개수를 계산합니다.  

len()

2. 계산한 정보를 반환하는 함수 `popular_count`를 완성합니다. 

   

### Problem B

Problem A에서 popular를 기준으로 가져온 영화 목록 중 평점이 8 이상인 영화들의 목록을 출력합니다. 

1. `requests`를 이용하여 인기 영화 정보(Get Popular)에 요청을 보냅니다.
2. 받아온 데이터에서 평점(key `vote_average`)를 기준으로 점수가 8 이상인 영화들의 목록을 리스트로 반환하는 함수 `vote_average_movies`를 완성합니다.



### Problem C

특정 조건에 맞는 인기 영화 조회 II 영화목록을 평점순으로 출력하는 함수를 완성합니다. 

1. `requests`를 이용하여 인기 영화 정보(Get Popular)에 요청을 보냅니다.
2. 받아온 데이터 중 평점(key `vote_average`)이 높은 영화 다섯개의 정보를 리스트로 반환하는 함수 `ranking`을 완성합니다. 



### Problem D

특정 영화 추천 영화 조회 제공된 영화 제목을 기준으로 추천영화 목록을 출력합니다.

1. `requests`를 이용하여 영화 검색(Search Movies) 요청을 보냅니다. (인자로 넘어온 `title` 사용)
2. 결과중 첫번째 영화가 검색한 영화가 맞다면 해당 영화의 id를 사용합니다.
3. id를 기반으로 추천영화 목록 조회 (Get Recommendations) URL을 생성합니다. 
4. `requests`를 이용하여 추천영화 목록 조회 URL에 요청을 보냅니다. 
5. 추천받은 영화 리스트에서 **제목만을** 리스트에 저장합니다. 
6. 저장된 리스트를 반환하는 함수 `recommendation`을 완성합니다. 
7. (2번) id값은 있지만 추천영화가 없는 경우 빈 리스트를 반환합니다. 
8. (3번) 올바르지 않은 영화 제목으로 검색할 수 없는 경우 `None`을 반환합니다. 



### 1번 답
``` python
import requests

key = '68c36bcac7f38b09c933975c8ce9c200'
url = 'https://api.themoviedb.org/3/movie/popular?api_key=68c36bcac7f38b09c933975c8ce9c200&language=en-US&page=1'
# string으로 된 문자를 dict으로 풀어준다.
data = requests.get(url).json()
data['results']

def popular_count(data):
    return len(data['results'])

popular_count(data)
```


### 2번 답

```python
data['results'][0]['vote_average']

for num in range(popular_count(data)):
    print(data['results'][num]['vote_average'])

    or num in range(popular_count(data)):
    if data['results'][num]['vote_average'] >= 8:
            print(data['results'][num]['vote_average'])

    for num in range(popular_count(data)):
    if data['results'][num]['vote_average'] >= 8:
            print(data['results'][num])


    gm = []

for num in range(popular_count(data)):
    if data['results'][num]['vote_average'] >= 8:
            gm.append(data['results'][num])
            
print(gm)


def vote_average_movies(data):
    good_movie = []
    for num in range(popular_count(data)):
        if data['results'][num]['vote_average'] >= 8:
            good_movie.append(data['results'][num])
    return good_movie

vote_average_movies(data)
```


### 3번
```python
movie = data['results']
sorted_films = sorted(movie, key = lambda film:film['vote_average'], reverse=True)


# 정렬된 영화리스트를 [0]~[4] 5개만 남겨주세요.
top5 = movie[0:5]

def ranking(data):
    movie = data['results']
    sorted_films = sorted(movie, key = lambda film:film['vote_average'], reverse=True)
    top5 = sorted_films[0:5]
    return top5

ranking(data)
```

### 4번

```python
# 영화 id를 이용해서 recommdation목록을 받기위한 요청을 보내세요.

url = f'https://api.themoviedb.org/3/movie/{id1}/recommendations?api_key={key}&language=en-US&page=1'
req = requests.get(url).json()
req

len(req['results'])


# recommendation 응답을 받은 데이터 중 original_title을 빈 리스트에 하나씩 append주세요

recommend = []
for num1 in range(len(req['results'])):
    recommend.append(req['results'][num1]['original_title'])  # recommend += 이런식으로 하려고 했지만, +는 스트링에서만 가능하고 list에서 하게 되면 그 안 구성요소 하나하나 더해진다
    
recommend


# 저장된 리스트를 반환하는 함수 recommendation을 완성합니다.
# 올바르지 않은 걸 입력하면 None 실제로 빈 리스트로 나오니 
# id값은 있지만 추천영화가 없는 경우 빈 리스트를 반환합니
#  컴퓨터야 data['results]가 []가 나오면 None 반환해줘


def recommendation(title):
    import requests
    key = '68c36bcac7f38b09c933975c8ce9c200'
    url = f'https://api.themoviedb.org/3/search/movie?api_key={key}&language=en-US&query={title}&page=1&include_adult=false'
    data = requests.get(url).json()
    
    film_data = data['results']
    
    if data['results'] == []:
        return None
                       
    id1 = film_data[0]['id']
    
    url = f'https://api.themoviedb.org/3/movie/{id1}/recommendations?api_key={key}&language=en-US&page=1'
    req = requests.get(url).json()
    
    if req['results'] == []:
        return []
    recommend = []
    for num1 in range(len(req['results'])):
        recommend.append(req['results'][num1]['original_title'])
    return recommend

    recommendation('asdf')
```