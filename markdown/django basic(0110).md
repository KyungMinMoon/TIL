venv : 가상환경

디렉토리 생성
mkdir mtv

생성한 디렉토리 들어가서 장고프로젝트 생성
django-admin startproject ~ .

앱 생성
django-admin startapp a

앱에 따른 페이지를 들어가면, error가 떠.
urls.py에 요청한 a url에 해당하는 매핑이 없기 때문 
 
urls.py 들어가서 a에 관한 path를 만들어줘
```
from a import views
path('a/', views.index),
  ** 콤마 빼먹지 말구!
```

views.py 들어가서 index 함수 추가하기
```
from django.http import HttpResponse
def index(request):
    return HttpResponse("~")

```

근데, url 추가할 때마다 계속 파일 수정해서 전체 프로젝트에 추가하기 귀찮고 어렵잖아.
path('a/', include('a.uls'))를 통해 귀찮음을 덜 수 있어.
a/ 페이지를 요청하면 config/urls.py가 아니라 a/urls.py를 만들어서 이게 열려서 이 파일만 수정하면 돼. 

그러니까,
a/urls.py 만들기

---
Model을 이용하여 //데이터베이스 처리//
- db가 필요한 앱은 꼭! migrate가 필요하다.
  
=> python manage.py migrate


앱들이 필요로 하는 db **테이블 생성**
python manage.py migrate

Q. 데이터베이스를 처리하는 방법이 테이블 생성인가? migrate의 역할이 테이블 생성?
아니아니
models.py에서 클래스 생성을 하면, 테이블이 만들어져.


a가 사용하는 모델을 만들어보자. 
a는 질문과 답변을 할 수 있는 게시판이라고 생각하면 돼.


질문을 하는 모델은
subject 질문 제목
content 질문 내용
created_date 질문을 작성한 일시

```
class Question(models.Modesl):
    subject = models.CharField(max_length=200)
    content = models.TextField()
    create_date = models.DateTimeField()
```

테이블 생성을 하기 위해서는
mtv/settings.py에 들어가서
'a.apps.mtvfolder', 
추가하기

---
block content/ endblock 하는 이유

html 기본 base를 상속받아 렌더링할 때, 특정 부분에 해당하는 부분만 상속받은 자식 html 내에서 원하는 양식으로 변경하고 싶을 때

ul(unordered list) : 순서가 없는 리스트
li(list item) : 요 리스트 안에 있는 아이템

---



render
request와 template_name 을 필수로 한다.
**템플릿을 불러오는 역할

redirect
어느 URL로 이동할지를 정하지만, context 값을 넘기지 못한다.
**URl로 이동하는 역할


classname.objects.all()
모든 데이터를 다 가져온다

