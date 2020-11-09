

```python
from sqlalchemy import create_engine
from sqlalchemy.orm import scoped_session, sessionmaker
from sqlalchemy.ext.declarative import declarative_base

from server.config import DATABASE_URL 

engine = create_engine(DATABASE_URL, echo=True) # 1

session = scoped_session(sessionmaker(autocommit=False, autoflush=False, bind=engine)) # 2

Base = declarative_base()
Base.query = session.query_property()

def init_db():
    import models
    Base.metadata.create_all(bind=engine)
```

1. 데이터베이스에 접속할 engine 객체를 선언한다.
  1. `echo=True` sqlalchemy가 생성한 query문을 보여준다	
2. 데이터베이스를 조작할 객체를 선언한다.

