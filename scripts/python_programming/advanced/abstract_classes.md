**1. 추상클래스(abstarct class)란**
추상클래스란 미구현 추상메소드를 한개 이상 가지며, 자식클래스에서 해당 추상 메소드를 반드시 구현하도록 강제합니다.
상속받은 클래스는 추상메소드를 구현하지 않아도, import할 때까지 에러는 발생하지 않으나 객체를 생성할 시 에러가 발생합니다.
추상클래스를 만들기 위한 형식은 아래와 같습니다.
반드시 abc 모듈을 import 해야합니다.
추상메소드는 생략하면 기본적인 클래스 기능은 동작합니다만, 추상메소드를 추가한 후에는 객체를 생성하면 에러가 발생합니다.

```py
  from abc import *
  class 추상클래스명(metaclass=ABCMeta):
    
       @abstractmethod
          def 추상메소드(self):
              pass
```
              
**2. 추상클래스(abstract class) 사용**
예제를 위해 ‘abstract.py’ 파일을 만들고, 아래의 코드를 작성합니다.

```py
  from abc import *
    
    
  class AbstractCountry(metaclass=ABCMeta):
      name = '국가명'
      population = '인구'
      capital = '수도'
    
      def show(self):
          print('국가 클래스의 메소드입니다.')
            
  class Korea(AbstractCountry):
    
      def __init__(self, name,population, capital):
          self.name = name
          self.population = population
          self.capital = capital
    
      def show_name(self):
          print('국가 이름은 : ', self.name)
```


아직 추상메소드를 작성하지 않았습니다.
하지만 추상클래스라할지라도 기본적인 클래스 기능은 동작합니다.(추상메소드를 작성하지 않았기때문에..)
상속한 객체도 생성이 됩니다.

```py
  >>> from abstract import *
  >>> a = AbstractCountry()
  >>> a.show()
  국가 클래스의 메소드입니다.
  >>> b = Korea("대한민국", 50000000, '서울')
  >>> b.show_name()
  국가 이름은 :  대한민국
  
AbstarctCountry 클래스에 추상메소드를 추가합니다.
  class AbstractCountry(metaclass=ABCMeta):
        
      ... 생략
        
      @abstractmethod
      def show_capital(self):
          print('국가의 수도는?')
          
```

         
다시 REPL 에서 상속받은 Korea 클래스 객체를 생성해봅니다.
객체 생성 시에 에러가 발생합니다.
Pycharm을 사용 중인데 에디터상에서 체크해서 경고를 해줄거라 기대했는데.. 에디터에서 weak warning으로 약한 회색줄만 살짝 그어져있군요, 유의해야합니다.

```py
  >>> from abstract import *
  >>> a = Korea("대한민국", 50000000, '서울')
  Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
  TypeError: Can't instantiate abstract class Korea with abstract methods show_capital

Korea 클래스에서 상속받은 추상메소드를 구현하겠습니다.
      class Korea(AbstractCountry):
        
         def show_capital(self):
             super().show_capital()
             print(self.capital)
            
          ... 생략
결과를 확인합니다.

  >>> from abstract import *
  >>> a = Korea("대한민국", 50000000, '서울')
  >>> a.show_capital()
  국가의 수도는?
  서울
추상메소드를 추가하고 객체를 생성하면 에러가 발생합니다.
  >>> from abstract import *
  >>> a = AbstractCountry()
  Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
  TypeError: Can't instantiate abstract class AbstractCountry with abstract methods show_capital
  
`    
