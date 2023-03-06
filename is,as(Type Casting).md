## 타입 캐스팅(Type Casting)이란?

타입 캐스팅은 인스턴스의 "타입"을 확인 or 해당 인스턴스를 슈퍼 클래스나 하위 클래스로 취급하는 방법.


### 1. is : Checking Type ###

- 타입을 체크하는 연산자 
- 표현식이 Type과 동일하거나, 표현식이 Type의 서브 클래스인 경우 -> true 그 외 -> false

```
let char: Character = "A"

char is Character             // true
char is String                // false
```

```
class Human { }
class Teacher: Human { }

let teacher: Teacher = .init()
teacher is Teacher            // true
teacher is Human              // true
```


```
class Human {
    let name: String
    init(name: String) {
        self.name = name
    }
}
class Teacher: Human { }
class Student: Human { }
 
 
let people: [Human] = [
    Teacher.init(name: "김선생"),
    Student.init(name: "박제자"),
    Student.init(name: "유제자")
]
```

Human 클래스를 상속받는 서브클래스 Teacher, Student.

아래처럼 타입 캐스팅을 통해 확인하면서 조건문을 분기할 수 있다.

```
for human in people {
    if human is Teacher {
        print("나는야 선생님 : \(human.name)")
    } else if human is Student {
        print("나는야 제자  : \(human.name)")
    }
}
```

### 2. as : Type Casting

(1) 업캐스팅(Upcasting)
 - 서브 클래스 인스턴스를 "슈퍼 클래스의 타입"으로 참조한다
 - 업 캐스팅은 항상 성공한다
 - as 연산자를 사용해서 할 수도 있다.

  아까 위에 예제에서 Teacher와 Student 클래스의 부모 클래스가 같은데 
  이 경우 둘의 슈퍼 클래스가 Human으로 동일하기 때문에
  이 둘을 Human이란 클래스로 "업캐스팅"해서 묶어버린 것.
  
  ```
  let human = Teacher.init() as Humann
  ```
  
  위 코드의 설명은 이러하다.
  " Teacher 타입의 인스턴스를 생성하지만, 이를 Human 타입으로 업캐스팅해서 human <<에 저장하겠다! "
  
  ```
  human.name             // Sodeul
  human.subject          // Value of type 'Human' has no member 'subject'
  ```
  
  이렇게 Human 클래스의 멤버인 name엔 접근할 수 있지만,
  서브 클래스 Teacher의 멤버인 subject엔 접근할 수 없음.!!!!!!!!
  

  => 한마디로, 서브 클래스의 인스턴스를 슈퍼 클래스의 타입으로 참조하는 것을 업캐스팅이라고 한다.
  
  as를 써서해도 되고, 직접 타입을 명시해도 된다.!
  
  ```
  // 1. as를 사용한 업캐스팅
let human1 = Teacher.init() as Human
 
  // 2. Type Annotation을 사용한 업캐스팅
let human2: Human = Teacher.init()
  ```
  
(2) 다운캐스팅(Downcasting)
  - 슈퍼 클래스 인스턴스를 "서브 클래스의 타입"으로 참조한다.
  - 업캐스팅된 인스턴스를 다시 원래 서브 클래스 타입으로 참조할 때 사용한다.
  - 다운 캐스팅은 "실패할 수 있음" 그래서 as?, as! 연산자를 이용한다.

  ```
  human.name             // Sodeul
  human.subject          // Value of type 'Human' has no member 'subject'
  ```
  위 코드는 아까 에러가 떴었음.
  
  그럼 제한된 Teacher란 서브 클래스의 subject 멤버에 접근하고 싶다면???????
  =====> " 다운 캐스팅 "
  
  `
var teacher: Teacher = human as! Teacher`

  이렇게 as연산자를 이용해서 
  Human 타입으로 업캐스팅된 human 변수를 다시 하위 클래스인 Teacher 타입으로 변환해서 넣어준 것!
  이것이 바로 다운캐스팅!!!!!!! (너 캐스팅된거야.)
  
  - 슈퍼 클래스인 Human 타입의 인스턴스를 서브 클래스인 Teacher 타입의 인스턴스로 참조하는 것 -

  `
  //쌉가능
let human: Human = Teacher.init()`


!!! 근데 실패할 수도 있잖아 !!!

그렇기 때문에 여기서 업캐스팅 is와 다르게 as에는 옵셔널(?, !)이 붙은 것이다 !

#### - as? : 런타임 시점에 타입 캐스팅(다운 캐스팅)을 하며, 실패할 경우 nil을 리턴
#### - as! : 런타임 시점에 타입 캐스팅(다운 캐스팅)을 하며, 실패할 경우 에러 발생


`for human in people {
   if let teaher =  human as? Teacher {
        print("나는야 선생님 : \(teacher.name)")
    } else if let student =  human as? Student {
        print("나는야 제자  : \(student.name)")
    }
}`

![image](https://user-images.githubusercontent.com/75918176/223109661-4b4be9a1-924b-4416-b4c3-7f11bf6f1209.png)


[내용출처] : https://babbab2.tistory.com/127
