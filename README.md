### mixer
---
https://github.com/klen/mixer

```py
from customapp.models import User, UserMessage
user = mixer.blend(User)
message = mixer.blend(UserMessage, user=user)
message = mixer.blend(UserMessage, user__username='testname')
some = mixer.blend('someapp.somemodel', somerelation=mixer.SELECT)
some = mixer.blend('someapp.somemodel', money=mixer.RANDOM)
some_models = mixer.cycle(5).blend('somemodel', company=(name for name in company_names))


from mixer.backend.flask import mixer
from models import User, UserMessage
mixer.init_app(self.app)
message = mixer.blend(UserMessage, user=user)
message = mixer.blend(UserMessage, user__username='testname')
some = mixer.blend('project.models.SomeModel', somerelation-mixer.SELECT)
some = mixer.blend('project.models.SomeModel', money=mixer.RANDOM)
some_models = mixer.cycle(5).blend('project.models.SomeModel', company=(company for company in compnies))


from mixer.backend.sqlalchemy import Mixer
class MyOwnMixer(Mixer):
  def populate_target(self, values):
    target = self.__scheme(**values)
    return target
  
mixer = MyOwnMixer()


from mixer.backend.sqlalchemy import mixer

ENGINE = create_engine('sqlite:///:memory:')
BASE = declarative_base()
SESSION = sessionmaker(bind=ENGINE)

mixer = Mixer(session=SESSION(), commit=True)
role = mixer.blend('package.models.Role')


from mixer.backend.mongoengine import mixer

class User(Document):
  created_at = DateTimeField(default=datetime.datetime.now)
  email = EmailField(required=True)
  first_name = StringField(max_length=50)
  last_name = StringField(max_length=50)
  username = StringField(max_length=50)
  
class Post(Document):
  title = StringField(max_length=120, required=True)
  author = ReferenceField(User)
  tags = ListField(StringField(max_length=30))
  
post = mixer.blend(Post, author__username='foo')


from mixer.main import mixer
import marshallow as ma

class User(ma.Schema):
  created_at = ma.fields.DateTime(required=True)
  email = ma.fields.Email(required=True)
  first_name = ma.fields.String(required=True)
  last_name = ma.fields.String(required=True)
  username = ma.fields.String(required=True)

class post(ma.Schema):
  title = ma.fields.String(required=True)
  author = ma.fields.nested(User, required=True)

post = mixer.blend(Post, author__username='foo')


from mixer.main import mixer

class Test:
  one = int
  two = int
  name = str
  
class Schema:
  name = str
  money = int
  male = bool
  prop = Test

schema = mixer.blend(Scheme, prop__one=1)

  
from mixer.backend.django import Mixer
mixer = Mixer(commit=False)


from mixer.backend.django import mixer
user1 = mixer.blend('auth.user')
with mixer.ctx(commit=False):
  user2 = mixer.blend('auth.user')

from mixer.main import mixer

class Test:
  id = int
  name = str
  
mixer.register(Test,
  name=lambda: 'John',
  id=lambda: str(mixer.faker.small_positive_integer())
)

test = mixer.blend(Test)
test.name == 'John'
isinstance(test.id, str)

mixer.register(Test, name='Just John')
test = mixer.blend(Test)
test.name == 'John John'

from mixer.backend.django import Mixer, GenFactory

def get_func(*args, **kwargs):
  return "Always same"

class MyFactory(GenFactory):
  generators = {
    models.CharField: get_func
  }

mixer = Mixer(factory=MyFactory)


from mixer.backend.django import mixer

@mixer.middleware('auth.user')
def encrypt_password(user):
  user.set_password('test')
  return user

mixer.unregister_middleware(encrypt_password)


from mixer.backend.django import Mixer

mixer = Mixer(locale='it')
mixer.faker.name()

mixer.faker.locale = 'cz'
mixer.faker.name()

mixer.faker.local = 'en'
mixer.faker.name()

mixer.faker.phone()
with mixer.ctx(locale='fr'):
  mixer.faker.phone()

mixer.faker.phone()
```

```
pip install mixer
```

```
```


