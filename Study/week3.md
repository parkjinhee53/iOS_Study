```swift
// 저장 타입 프로퍼티의 경우 선언할 당시 원하는 값으로 항상 초기화가 되어 있어야 한다

struct structTemp {
    static var type1 = "11"
    static let type2 = "22"
    static var type3: String {
        return "33"
    }
}

class classTemp {
    init() {
        print("init..")
    }
    deinit {
        print("deinit..")
    }

    static var type1 = "aa"
    static let type2 = "bb"
    static var type3: String {
        return "33"
    }
}

var st = structTemp()

var ct = classTemp()

// get set
structTemp.type1 = "change 11"
// const
//structTemp.type2 = "change 22"
// get-only
//structTemp.type3 = "change 33"

// get set
classTemp.type1 = "change 11"
// const
//classTemp.type2 = "change 22"
// get-only
//classTemp.type3 = "change 33"

structTemp.type1
classTemp.type1

protocol Something2: AnyObject {
    var someValue2: Int? { get set }
    func doSomething2()
}

protocol Something: AnyObject {
    func doSomething()
    var two: Something2? { get set }
    var three: SomeClass3? { get set }
    var someValue: Int? { get set }
}

class SomeClass2: Something2 {
    var someValue2: Int?

    init() {
        print("init")
    }
    deinit {
        print("deinit")
    }

    func doSomething2() {
        print(someValue2)
    }
}

class SomeClass3 {
    init() {
        print("init..,,")
    }
    deinit {
        print("deinit..,,")
    }
}

class SomeClass: Something {
    weak var two: Something2?
    weak var three: SomeClass3?
    var someValue: Int?

    init() {
        print("init..")
    }
    deinit {
        print("deinit..")
    }

    func doSomething() {
        print(someValue)
    }
}

var temp1: Something? = SomeClass()
var temp2: Something2? = SomeClass2()
var temp3: SomeClass3? = SomeClass3()

temp1?.three = temp3
temp3 = nil

temp1?.two = temp2
temp2 = nil

temp1.someValue = 10
temp1.someValue
temp1.doSomething()

temp2.someValue
temp2.doSomething()

//protocol Vehicle {
//    var name: String { get set }
//    var maxFuel: Int { get set }
//
//    func start()
//}
//
//class Car: Vehicle {
//    var name: String
//    var maxFuel: Int
//
//    init(name: String, maxFuel: Int) {
//        self.name = name
//        self.maxFuel = maxFuel
//    }
//
//    func start() {
//        print("자동차 시동걸기..")
//    }
//
//    func forward() {
//        print("앞으로 가기..")
//    }
//}
//
//class Airplane: Vehicle {
//    var name: String
//    var maxFuel: Int
//
//    init(name: String, maxFuel: Int) {
//        self.name = name
//        self.maxFuel = maxFuel
//    }
//
//    func start() {
//        print("비행기 시동걸기..")
//    }
//
//    func fly() {
//        print("날아가기..")
//    }
//}

//protocol Runable {
//    var velocity: Int { get set }
//}
//
//protocol Talkable {
//    var text: String { get set }
//}
//
//protocol Flyable {
//    var flightTime: Int { get set }
//}
//
//protocol Swimable {
//    var diveTime: Int { get set }
//}
//
//class Person: Runable, Talkable, Swimable {
//    var velocity: Int = 7
//
//    var text: String = "Hello"
//
//    var diveTime: Int = 60
//}
//
//class Frog: Runable, Swimable {
//    var velocity: Int = 3
//
//    var diveTime: Int = 600
//}
//
//class Bird: Flyable {
//    var flightTime: Int = 1000
//
//    func feed() {
//        print("모이 주기~")
//    }
//
//    init() {
//        print("init..")
//    }
//}
//
//var hawk: Flyable = Bird()
//
//hawk.flightTime

// MARK: - delegate pattern
//
//// 청사진
//
//// 1 클래스만 채택하기 위해서
//// struct enum class
//protocol changing: AnyObject {
//    func getData(plus n: Int)
//}
//
//
//
//// a->b->a로 화면을 이동하며 b의 데이터를 다시 a로 보낼거임
//// 나는 b로 화면을 이동할거야.
//class aVC: changing {
//    func getData(plus n: Int) {
//        print(10 + n)
//    }
//
//    let num = 10
//
//    // 야 클릭해서 가는 뷰 보고 내가 일한다 그래라
//    func onClick(b: bVC) {
//        // 주소복사
//        b.delegate = self
//    }
//
//    func onCClick(c: cVC) {
//        c.delegate = self
//    }
//}
//
//class cVC {
//    weak var delegate: changing?
//
//    func sendData() {
//        delegate?.getData(plus: 15)
//    }
//}
//
//// 나는 데이터를 받아서 출력할거야
//class bVC {
//    // a가 대신 일한다는 정보를 담고 있음.
//    // weak 타입, 프로토콜 타입.
//    weak var delegate: changing?
//
//    // 그래 니가 일 대신하셈 이거 일하면 됨.
//    func sendData() {
//        delegate?.getData(plus: 10)
//    }
//}
//
//let a = aVC()
//let b = bVC()
//let c = cVC()
//a.onClick(b: b)
//b.sendData()
//a.onCClick(c: c)
//c.sendData()

// POP
// MARK: - protocol extension
protocol Printing {
    // 타입 프로퍼티
    static var print: String { get set }
    var top: Int { get set }
}

extension Printing {
    // 연산 프로퍼티
    var text: String { return "Hello" }
    public func log() -> String {
        return "log: "
    }
}

class c: Printing {
    static var print: String = "LOG"
    
    var top: Int = 10
    
    init() {
//        print(log())
    }
}
c.print
let ci = c()
ci.text



// MARK: - 예시
//// 프로토콜: 무슨 일을 할 거니?
//protocol PrepareParty: AnyObject {
//    func prepareFood()
//    func prepareSong()
//}
//
//// 나는 실질적으로 주문을 하는 놈이야
//class PartyDirector {
//    weak var delegate: PrepareParty?
//
//    init() {
//        print("init")
//    }
//
//    deinit {
//        print("deinit")
//    }
//
//    func order() {
//        self.delegate?.prepareFood()
//        self.delegate?.prepareSong()
//    }
//}
//
//// 프로토콜을 채택해서 자세한 내용을 구현할거야 그리고 이 역할을 해줄놈은 따로있어.
//class FirstPartyWorker: PrepareParty {
//    func prepareFood() {
//        print("1food~")
//    }
//
//    func prepareSong() {
//        print("1song~")
//    }
//
//    init(director: PartyDirector) {
//        director.delegate = self
//    }
//}
//
//// 프로토콜을 채택해서 자세한 내용을 구현할거야 그리고 이 역할을 해줄놈은 따로있어.
//class SecondPartyWorker: PrepareParty {
//    func prepareFood() {
//        print("2food~")
//    }
//
//    func prepareSong() {
//        print("2song~")
//    }
//
//    init(director: PartyDirector) {
//        director.delegate = self
//    }
//}
//
//var mojito: PartyDirector? = PartyDirector()
//
//// "김"은 어떻게 일할 지를 담아서 mojito에게 넘겨줬어.
//let kim = FirstPartyWorker(director: mojito!)
//
//mojito?.order()
//
//// "초"는 어떻게 일할 지를 담아서 mojito에게 넘겨줬어.
//let cho = SecondPartyWorker(director: mojito!)
//
//mojito?.order()
//
//mojito = nil
```
