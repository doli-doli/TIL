### MVC
- MVC의 기본 개념 이해
## M(Model) - 자바
#### 서비스클래스 or 자바빈(model 2)
- 모델(model)이란 어떠한 동작을 수행하는 코드를 말한다.
- 모델은 순수하게 public 함수로만 이루어진다.
## V(View) - JSP
#### JSP페이지(model 2)
- 모델은 여러 개의 뷰(view)를 가질 수 있다.
- 뷰는 모델에게 질의를 하여 모델로 부터 값을 가져와 사용자에게 보여준다.
## C(Controller) - Servlet
#### Servlet(model 2)
- 뷰는 여러 개의 컨트롤러(Controller)를 가지고 있다.
- 사용자는 컨트롤러를 사용하여 모델의 상태를 바꾼다.
- 컨트롤러는 모델의 mutator 함수를 호출하여 상태를 바꾼다.
