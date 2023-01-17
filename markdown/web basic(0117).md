models.py

```python
from django.db import models

class Person(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField(default=20)

    def __str__(self):
        return f'{self.pk}: {self.name}'


class Feed(models.Model):
    author = models.ForeignKey(Person, on_delete=models.CASCADE, related_name='feeds')
    content = models.TextField()
    like_people = models.ManyToManyField(Person, related_name='like_feeds')


class Comment(models.Model):
    author = models.ForeignKey(Person, on_delete=models.CASCADE)
    feed = models.ForeignKey(Feed, on_delete=models.CASCADE)
    content = models.CharField(max_length=300)
```

'''
p1 = Person.objects.create(name='neo', age='23')
p2 = Person.objects.create(name='justin', age=25)
p3 = Person.objects.create(name='alex', age=23)

f1 = Feed.objects.create(content='콧물이난다..', author=p1)
c1 = Comment.objects.create(content='훌쩍..', feed=f1, author=p2)


    [related_name]
p1. like_feeds. all()  # 좋아요 한 게시글 모두
    
    [field_name]
f1. like_people .all()  # 좋아요 한 사람들 모두



p1.like_feeds.add(f1)  # p1이 좋아요 한 게시글에 f1 추가 = > join 테이블에 p1, f1 레코
f1. like_people.add(p1)  #결과 같음(데이터 중복 안 됨)

p1.like_feeds.remove(f1)  # join 테이블에서 p1, f1으로 구성된 레코드 삭제
f1.like_people.remove(p1)  # 결과 같음
'''


```python
from django.db import models

class Lecture(models.Model):
    title = models.CharField(max_length=100)
    room = models.CharField(max_length=100)
    def __str__(self):
        return f'#{self.pk}: {self.title}'
        

class Student(models.Model):
    name = models.CharField(max_length=30)
    major = models.CharField(max_length=30)
    lectures = models.ManyToManyField(
        Lecture,                      # m:n 관계의 상대 모델
        related_name='students',      # 상대 모델(Lecture)이 나(Student)를 부를 때 이름
        through='school.Enrollment',  # 커스텀 중개모델 이름(str)
        through_fields=('student', 'lecture')  # M:N을 맺는 FK들 명시
    )
    def __str__(self):
        return f'#{self.pk}: {self.name}'


# Join Table에 추가 데이터가 있다면, 클래스 생성
class Enrollment(models.Model):
    lecture = models.ForeignKey(Lecture, on_delete=models.CASCADE)
    student = models.ForeignKey(Student, on_delete=models.CASCADE)
    grade = models.CharField(max_length=2)
    semester = models.CharField(max_length=20)

    def __str__(self):
        return f'{self.student} => {self.lecture}'


'''

# 자동으로 Enrollment의 객체가 생성이 됨(권장 X)
s1.lectures.add(l1)

# 방금 생성된 Enrollment 객체 조회
e1 = Enrollment.objects.get(student=s1, lecture=l1)

e1.student == s1
e1.lecture == l1

# 자동 생성 시 비어있는 항목들
e1.grade == ''
e1.semester == ''

e1.grade = 'B'
e1.semester = '2023-1'

# 수강신청을 새로 생성
Enrollment.objects.create(
    student=s1,
    lecture=l2,
    grade='C+'
    semester='2023-1'
)

# s1의 모든 수업
s1.lectures.all()

# l2의 모든 수가앵
l2.students.all()
'''

acco/model
from django.db import models
from django.contrib.auth.models import AbstractUser


class User(AbstractUser):

    def __str__(self):
        return self.username


from django.db import models
from django.conf import settings


class Article(models.Model):
    user = models.ForeignKey(
        settings.AUTH_USER_MODEL,
        on_delete=models.CASCADE
    )
    like_users = models.ManyToManyField(
        settings.AUTH_USER_MODEL,
        related_name='like_articles'
    )
    title = models.CharField(max_length=100)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)


class Comment(models.Model):
    user = models.ForeignKey(
        settings.AUTH_USER_MODEL,
        on_delete=models.CASCADE
    )
    content = models.CharField(max_length=200)
    # foreign key 쓰면 필드명에 _id 붙이지 않기.
    # migrate 하면 알아서 뒤에 _id 붙음.
    article = models.ForeignKey(Article, on_delete=models.CASCADE)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
