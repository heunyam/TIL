# [아키텍처 패턴] MVC

Flask 프레임워크를 MVC 패턴을 적용해서 개발하고 있다. 내가 제대로 사용하고 있는지, 개선할 부분은 없는지 MVC 패턴에 대해서 알아보기로 했다,

## MVC란?

소공에서 사용되는  소프트웨어 디자인 패턴이다. 일종의 개발 규칙이라고도 볼 수 있다.

사용자 인터페이스로 부터 비즈니스 로직과 UI 로직을 분리해서 유지보수를 독립적으로 수행할 수 있게 하는 것이다.

> 비즈니스 로직이란 데이터를 생성·표시·저장·변경하는 부분을 일컫는다

### 1. Model

Model이란 어플리케이션의 데이터, 자료를 의미한다.

백엔드에서는 DB, 그리고 DAO와 DTO에 해당하는 부분이다.

### 2. View

View는 사용자에게 보여지는 부분, 즉 유저 인터페이스를 의미한다.

### 3. Controller

Model과 View사이를 이어주는 비즈리스  로직이 존재하는 부분이다.



## Flask 에서는?

### 왜 하필 MVC?

Flask는 Django와 다르게 프레임워크 자체에서 강요하는 패턴이 없기 때문에 개발자가 자유롭게 여러 패턴을 적용시킬 수 있다. 공부하는 입장에서는 최고의 장점이다.

두가지 선택지 MVC와 3 Layer 아키텍쳐 중 MVC를 사용하게 되었다.

>server/ (src root folder)
>
>​	model/
>
>​	controller/
>
>​    view/
>
>​    \_\_init\_\_.py
>
>​	app.py
>
>​    router.py
>
>​    setapp.py



### Model

- `sqlalchemy orm`를 사용한다

### View

- `Blueprint`와 `flask_restful`을 이용한다.

### Controller

- 비즈니스 로직이 존재한다.
- View에서 Controller에 있는 함수를 호출하고 Controller는 Model에서 정의한 데이터베이스 모델을 통해 데이터에 접근한다.

### 문제점?

내가 MVC 패턴을 적용하면서 느낀 문제점이다.

1. controller 범위
   - V와 M이 아닌면서 비즈니스 로직이 아닌 부분도 controller에 넣게 되었다.





















