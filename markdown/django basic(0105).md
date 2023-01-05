* Application definition
- python manage.py startapp <App> => 바로 등록부터 하기
- 
** django-admin startproject <project-name>은 프로젝트를 만들고, 그 안에서 python manage.py startapp review 명령어로 app을 시작해.

** 서버라는 아이는 req를 보내고 res를 받는 서빙하는 아이야. 
req를 하는 것은 URL!! url은 pattern을 만들어야 해. 
일을 하려면 함수도 필요하고, 그건 views.py에서 해. 
res를 서빙하는 건 html로!


**MTV

Model(DB)
Template(HTML)
View(controller)

```
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        * django는 기본적으로 app 안에 templates/ 폴더에서 HTML을 찾는다.
        'DIRS': [],  * django가 추가로 HTML을 찾아볼 폴더 등록


```

## review urls.

```
from django.urls import path
from . import views

* 변수명 반드시 app_name으로 똑같이 해야해!!
app_name = 'review'


* URL 구성 맨 앞에 'review/'는 이미 master url에서 검사가 끝남.
urlpatterns = [
    # 패턴 '(review/)index/'가 요청으로 들어온다면, index 함수 실행!
    path('', views.index, name='index'),
    path('hello/', views.hello, name='hello'),
]


# review/hello/ => view hello 함수 실행 => hello.html을 응답(렌더)
```


### urls.py

```html
from django.urls import path
from . import views

app_name = 'data'

urlpatterns = [
    # data/
    path('', views.index, name="index"),
    # data/hello/<name>/ => variable Routing
    path('hello/<str:name>/', views.hello, name='hello'),

    # hello/neo/ => 안녕 neo,
    # hello/andy/ => 안녕 andy,


    # data/user_input/
    path('user_input/', views.user_input, name='user_input'),

    path('user_output/', views.user_output, name='user_output')
]

```

### views.py
```html
from django.shortcuts import render

def index(request):

    return render(request, 'data/index.html')

def hello(request, name):
    context = {
        'name' : name,
    }
    return render(request, 'data/hello.html', context)

def user_input(request):

    return render(request,'data/user_input.html')

def user_output(request):
    print(request.POST['username'], request.POST['password'])  #딕셔너리다
    return render(request, 'data/user_output.html')
```

### hello.html
```html
{% include 'base.html' %}

{% block content %}
<h1>안녕, {{name}}</h1>
{% endblock content %}
```

### user_input.html

```html
{% include 'base.html' %}

{% block content %}
<h1>User Input</h1>

<form action="{% url 'data:user_output' %}" method="POST">
    {% csrf_token %}
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="submit">
</form>



{% endblock content %}
```