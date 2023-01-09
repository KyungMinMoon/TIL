python include django, requests, flask, jupyter, ipython

python -m venv venv(MTV라는 폴더를 만들고, 바깥 폴더인 global python에서 django를 가져올 수 없으니 이 명령어를 통해 mtv안에 'venv/'라는 폴더를 만든다.)

만약에 다시 global python을 가져오게 하고 싶다면, 'deactivate'명령어를 입력하면 됨.

source venv/Scripts/activate
pip install django==3.2.16
django-admin startproject mtv .

이렇게 하면
=> mtv라는 폴더 안에 manage.py mtv venv 생김

model.py은 class와 대응한다. 게시판 안에 id와 content를 먼저 작성한다.






post는 DB에 변경이 일어날 때 사용!!




















* models.py
```python
from django.db import models

class Article(models.Model):
    # id는 자동생성됨. 신경 쓰지 마세요.
    title = models.CharField(max_length=200)
    Content = models.TextField()
    # 생성시 자동으로 채워지도록 하고 싶음
    created_at = models.DateTimeField(auto_now_add=True)
    # 생성/수정시 자동으로 채워지도록 하고 싶음
    updated_at = models.DateTimeField(auto_now=True)
```