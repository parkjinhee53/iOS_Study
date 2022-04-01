```swift
// ARC
class Person {
    let name: String
    init(name: String) {
        self.name = name
        print("\(name) is being initialized")
    }
    deinit {
        print("\(name) is being deinitialized")
    }
}
var reference1: Person?
var reference2: Person?
var reference3: Person?

reference1 = Person(name: "Kim")
reference2 = reference1
reference3 = reference1

reference1 = nil

// 기본 클로저 형태
func closure1() {
    let message = "Hello World!"

    let num = 10
    let closure = { print(num) }

    print(message)
}

closure1()

// Reference Capture
func closure2() {
    var num: Int = 0
    print("num check #1 = \(num)")

    let closure = {
        print("num check #3 = \(num)")
    }

    num = 20
    print("num check #2 = \(num)")
    closure()
}

closure2()

// Value Capture
func closure3() {
    var num: Int = 0
    print("num check #1 = \(num)")

    // Const Value Type!
    let closure = { [num] in
        print("num check #3 = \(num)")
    }

    num = 20
    print("num check #2 = \(num)")
    closure()
}

closure3()

// Reference Type Value Capture
class Person {
    var name: String = "Kim"
}

var person = Person()

let closure = { [person] in
    print(person.name)
}

person.name = "Unknown"
closure()

// ARC Closure
class Person {
    var name = ""

    init(name: String) {
        self.name = name
    }

    deinit {
        print("person 죽음..")
    }

    lazy var getName: () -> String = {
        // ARC ++
        return self.name
    }
}

var person: Person? = Person(name: "Kim")
print(person!.getName())

person = nil

// Strong Weak Unowned

class Person {
    let name: String
    weak var friend: Person?
    init(name: String) {
        self.name = name
        print("\(name) is being initialized")
    }
    deinit {
        print("\(name) is being deinitialized")
    }
}

var kim: Person? = Person(name: "kim")
var lee: Person? = Person(name: "lee")

kim?.friend = lee
lee?.friend = kim

kim = nil
lee = nil

class Person {
    var name = ""

    init(name: String) {
        self.name = name
    }

    deinit {
        print("person 죽음..")
    }

    lazy var getName: () -> String = { [unowned self] in
        // ARC x
        return self.name
    }
}

var person: Person? = Person(name: "Kim")
print(person!.getName())

person = nil

// Weak Unowned

// 참조키워드 3가지
// protocol POP OOP


// 1. 똑같은 앱을 타이머, 계산기

// 스토리보드, 안쓰는
```
