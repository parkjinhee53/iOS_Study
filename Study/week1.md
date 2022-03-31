```swift
import CoreFoundation
import Darwin

// MARK: - Collection Types에는 어떤 것이 있는가?

// Array
var array1: [Int] = [1, 2, 3, 4, 5]
var array2 = [Int](arrayLiteral: 1, 2, 3, 4, 5)

var array3: [[Int]] = []
var array4: [[Int]] = [[Int]].init(repeating: [Int].init(repeating: 0, count: 5), count: 5)

//for i in array1 {
//    print(i)
//}

type(of: array1)
type(of: array2)
type(of: array3)
type(of: array4)

// Set
var set1: Set<Int> = [1, 2, 3, 4, 5]
var set2 = Set<Int>(arrayLiteral: 1, 2, 3)

set1.union(set2)
set1.subtracting(set2)
set1.intersection(set2)

//for i in set1 {
//    print(i)
//}

// Dictionary
var dictionary1 = [Int: String](dictionaryLiteral: (1, "a"), (2, "b"))
var dictionary2: [Int: String] = [1: "a", 2: "b"]

//for i in dictionary1 {
//    print("\(i.key), \(i.value)")
//}

dictionary1.keys
dictionary1.values

// MARK: - Controll Flow에는 어떤 것이 있는가?

let flow = [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]

//for i in flow {
//    print(i)
//}

//for i in 5..<flow.count {
//    print(flow[i])
//}

//for i in 5...flow.count {
//    print(flow[i])
//}

//for i in stride(from: 0, to: 10, by: 3) {
//    print(flow[i])
//}

//twiceLoop: for i in 0..<10 {
//    for j in 0..<10 {
//        print("\(i)" + " \(j)")
//        if i == 5 && j == 5 {
//            break twiceLoop
//        }
//    }
//}

// MARK: - Optional이란 무엇인가?

// nil
var op1: Int? = 5
//print(op1)

var op2: Int = 0
//op2 = op1
//op2 = op1 ?? -1
//op2 = op1!

//if let op1 = op1 {
//    op2 = op1
//}


// MARK: - struct와 class의 차이는 무엇인가?

struct SimpleStruct {
    var count = 0
}

var SS1 = SimpleStruct()
var SS2 = SS1

SS1.count
SS2.count

SS1.count = 5

SS1.count
SS2.count


class SimpleClass {
    var count = 0
}

var SC1 = SimpleClass()
var SC2 = SC1

SC1.count
SC2.count

SC1.count = 5

SC1.count
SC2.count


// ARC

class Person {
    var name: String
    init(name: String) {
        self.name = name
        print("\(name) is being initialized")
    }
    deinit {
        print("\(name) is being deinitialized")
    }
}

var kim1: Person? = Person(name: "kim")

var kim2 = kim1
var kim3 = kim1

kim1?.name = "lee"

kim2?.name
kim3?.name

kim1 = nil

kim2?.name
kim3?.name

// 과제 ARC

// swift run

```
