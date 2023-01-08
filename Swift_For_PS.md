<Swift 알고리즘에 필요한 기초 문법들 총정리>
---
The king will be made. 
  
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
let nums = readLine()!.split(seperator:" ")
// ["1", "2", "3", "4"]
// split()를 이용한 쪼개기
```
```
let nums = readLine()!.components(seperateBy:" ") 
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

