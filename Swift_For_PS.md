<Swift 알고리즘에 필요한 기초 문법들 총정리>
---

![swift blackman](https://us.123rf.com/450wm/ismagilov/ismagilov1701/ismagilov170100268/68263757-%EA%B7%B8%EC%9D%98-%EB%91%90%EA%B1%B4%EC%9D%84-%ED%8D%BC-%ED%8C%85-%ED%95%98-%EA%B3%A0-%EA%B7%B8%EC%9D%98-%EB%85%B8%ED%8A%B8%EB%B6%81-%ED%99%94%EB%A9%B4%EC%97%90%EC%84%9C-%EC%B0%BE%EA%B3%A0-%EA%B9%8C%EB%A7%88%EA%B7%80%EC%97%90-%EC%95%84%ED%94%84%EB%A6%AC%EC%B9%B4-%EA%B3%84-%EB%AF%B8%EA%B5%AD%EC%9D%B8-%ED%95%B4%EC%BB%A4%EC%9D%98-%EB%8B%AB%EC%8A%B5%EB%8B%88%EB%8B%A4-%EC%BD%94%EB%94%A9%EC%9D%98-%EA%B0%9C%EB%85%90%EC%9E%85%EB%8B%88%EB%8B%A4-%EB%AA%A8%EC%9D%98.jpg?ver=6)
  
 ### The king will be made. 
  
**#1. 키보드 입력 받기**
--
```
let value = readLine()!
```

readLine() 리턴값은 Optional String. 
-> 값이 들어갈 수도 있고~ 안들어갈 수도 있고~ 지만!!!
   알고리즘문제에서 입력값은 무조건 주어지기 때문에 강제 언래핑을 해주는게 좋음.
   그래서 '!'로 언래핑해주자  

**#1-1. 키보드 입력받은 값 공백으로 구분하기**
--
입력 : 1, 2, 3, 4

```
let nums = readLine()!.split(separator:" ")
// ["1", "2", "3", "4"]
// split()를 이용한 쪼개기
```
```
let nums = readLine()!.components(separateBy:" ") 
// ["1", "2", "3", "4"]
// component()를 이용한 쪼개기
```
***둘의 차이***  
1. Import Foundation  
-> split()은 스위프트 기본 instance method라서 그냥 사용 가능    
-> component()는 Foundation에 들어가있는 method라서 import 해야 사용 가능
2. 리턴값 타입이 다름   
-> split : [String.SubSequence] 타입이라 스플릿으로 쪼개면 바로 String으로 사용 불가.  
(map 해야함)  
-> components : [String] 타입  

---

**#1-2. 띄어쓰기로 정수 여러개 입력 받기**
```
let input = readline()!.split(separator: " ").map {
  Int(String($0))! }
//입력 : 1 2 3
// Array<Int>
// [1, 2, 3]
// .map : 맵 클로저 안의 코드를 배열 하나하나의 아이템에 적용시킨다.
```

**#1-3. 입력 받는 방법 총정리
```
알고리즘 풀면서 입력을 안 받는 경우는 없음.. 편의를 위해 readLine에서 옵셔널 강제 해제를 해준다.

// 문자열을 한 줄 받으려면!
let input = readLine()!

// components로 뒤에 인자로 들어가는 문자 (여기서는 공백)을 기준으로 문자열을 잘라 배열 형식으로 저장한다.
let input = readLine()!.components(separatedBy: " ")

// Int형 받기 -> 단순 형변환!
let input = Int(readLine!())

// Int값이 공백을 기준으로 하나씩 들어온다 -> map을 이용한 형 변환, 저장은 배열 형태!
let input = readLine()!.components(separtedBy: " ").map({ Int($0) })
```


**#2. 배열(Array) 다루기**
--

````
var empty: [Int] = []
var empty = [Int]()
var empty : Array<Int> = []
//빈 배열 만들기
````

````
var array = Array(1...5) // [1,2,3,4,5]
//임의의 date 넣어서 만들기
````

````
var arr = Array(repeating: 0, count: 3) //[0,0,0]
//크기가 정해진 배열 생성
````

````
let matrix = [[Int]]()

let matrix2: [[Int]] = Array(reapting:Array(repeating:1, count: 5), count: 3)
// 안쪽 count가 행, 바깥 count가 열

arr[i][j] // 다룰 때
````

````
array.reversed()
//배열 거꾸로 출력
````

````
array.sorted() // default는 오름차순
array.sorted(by: >) // 내림차순 
````

#2-1. map, filter, reduce(배열에서 중요한 세 가지)
--
````
var string = ["1", "2", "3", "4"]
string.map { Int($0)! } // [1,2,3,4] 각 원소를 전부 Int로 맵핑
````

````
var array = [1,2,3,4]
array.filter { $0 % 2 == 0 } // [2,4] 조건에 맞는 수만 뽑아냄.
````

````
var array = [1,2,3,4]
array.reduce(0, +) // 숫자 합이 나타남. 문자열 합치기도 가능
````

