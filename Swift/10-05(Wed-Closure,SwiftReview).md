
- 
    
   ![Untitled - 2022-10-06T165354 781](https://user-images.githubusercontent.com/67450169/194249788-3a2fcba7-dcd1-4e11-9a92-00dfeec0049c.png)
    ## πΈSwift 5.7 μ κΈ°λ₯
    
    ```swift
    // μ΅μλμ΄ λλ©΄ nil κ°μ΄ λ  μλ μκ³  μλ μλ μλ€
    var name: String?
    
    if let myName = name {
        print("\(myName)")
    } else {
        print("nilμλλ€")
    }
    
    name = "ned"
    
    if let name = name {
        print("\(name)")
    } else {
        print("nilμλλ€")
    }
    
    // Swift 5.7μ μ κΈ°λ₯!
    if let name {
        print("\(name)")
    } else {
        print("nilμλλ€")
    }
    ```
    
    ```swift
    //guard Swift 5.7 μ κΈ°λ₯!
    func sayHello(name: String?) {
        guard let name else {
            return print("nilμλλ€")
        }
        
        print("Hello World!")
    }
    
    sayHello(name: "ned")
    sayHello(name: nil)
    ```
    
    ```swift
    //guard Swift 5.7 μ κΈ°λ₯!
    func sayHello(name: String?) {
        guard let _ = name else {
            return print("nilμλλ€")
        }
        
        print("Hello World!")
    }
    
    sayHello(name: "ned")
    sayHello(name: nil)
    ```
    
    ## πΈSwiftμ ν΄λ‘μ 
    
    - μ»΄ν¨ν° κ³΅ν μ©μ΄μμμ **ν΄λ‘μ **λ ν¨μλ ν΄λ‘μ  ννμκ³  γκ°μ λλ¦½μ μΈ μ½λλΈλ‘κ³Ό μ½λλΈλ‘ μ£Όλ³μ μλ νλ μ΄μμ λ³μκ° κ²°ν©λ κ²μ λ§νλ€.
    - μ€λ₯Έμͺ½ μ½λμμ **functionA**λ **functionB**λΌλ μ΄λ¦μ ν¨μλ₯Ό λ°νλλ€.
    - μ¬μ€ **functionB**λ **functionB** λ΄λΆ μμ­ λ°μ μ μΈλ counter λ³μμ μμ‘΄νκΈ° λλ¬Έμ **functionA**λ ν΄λ‘μ λ₯Ό λ°ννκ³  μλ€.
    - λ€μ λ§ν΄, **functionB**λ counter λ³μλ₯Ό μ‘κ³ μλ€ λλ κ°λκ³  μλ€ λΌκ³  λ§ν μ μμΌλ―λ‘ μ ν΅μ μΈ μ»΄ν¨ν° κ³΅ν μ©μ΄μΈ ν΄λ‘μ λ‘ κ°μ£Όνλ€.
    - Swiftμμλ **ν΄λ‘μ **μ **ν΄λ‘μ  ννμ**μ©μ΄κ° νΌμ©λκΈ° μμνμ§λ§, μ΄μ¨λ  λ λ€ μ§μνλ€.
    
    ```swift
    func functionA() -> Int {
        
        var counter = 5
        
        // functionA ν¨μ μμ functionB ν¨μ μ μΈ - μ€μ²©λ ν¨μ
        func functionB() -> Int {
            // functionB λ°μ counterλ₯Ό μ¬μ©ν κ³μ°κ°μ λ°ννλ€
            return counter + 30
        }
        
        let result = functionB()
        print("\(result)")
        
        
        return 10
    }
    
    let result = functionA()
    print("\(result)")
    ```
    
    ```swift
    // κ°λ¨ν ν΄λ‘μ  μμ 
    
    func functionA() -> () -> Int {
        
        var counter = 5
        
        // functionA ν¨μ μμ functionB ν¨μ μ μΈ - μ€μ²©λ ν¨μ
        func functionB() -> Int {
            // functionB λ°μ counterλ₯Ό μ¬μ©ν κ³μ°κ°μ λ°ννλ€
            return counter + 30
        }
        
        let result = functionB()
        print("\(result)")
        
        // functionB() μ΄κ²μ functionBλ₯Ό νΈμΆνλ λ¬Έκ΅¬
        // functionB   μ΄κ²μ functionB ν¨μ κ·Έ μμ²΄λ₯Ό μ§μΉ­ν¨
        return functionB
    }
    
    // functionA() νΈμΆμ κ²°κ³Όλ functionB ν¨μμ΄κ³ 
    // functionB ν¨μ μμλ counterκ°μ΄ κ³μ λΆμ‘ν νμ©μ΄ λλ€
    // myClosureκ° κ³§ functionBμ΄κΈ° λλ¬Έμ myClosureκ° μ‘΄μ¬νλ λμ counterλ λΆμ‘ν μ‘΄μ¬νλ€
    let myClosure = functionA()
    let result = myClosure()
    print("\(result)")
    ```
    
    ---
    
    ```swift
    // λ°°μ΄ μ λ ¬ μμ 
    let names = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]
    var defaultNames = names.sorted()
    print(defaultNames)
    
    // μ λ ¬ κΈ°μ€μ λ§λ€μ΄μ£Όλ ν¨μ λ§λ€κΈ°
    func backward(_ s1: String, _ s2: String) -> Bool {
        print("\(s1)κ³Ό \(s2)λ₯Ό λΉκ΅ν©λλ€")
        return s1 > s2
    }
    
    var reverseNames = names.sorted(by: backward)
    print(reverseNames)
    /*
     Alexκ³Ό Chrisλ₯Ό λΉκ΅ν©λλ€
     Ewaκ³Ό Alexλ₯Ό λΉκ΅ν©λλ€
     Ewaκ³Ό Chrisλ₯Ό λΉκ΅ν©λλ€
     Barryκ³Ό Alexλ₯Ό λΉκ΅ν©λλ€
     Barryκ³Ό Chrisλ₯Ό λΉκ΅ν©λλ€
     Daniellaκ³Ό Alexλ₯Ό λΉκ΅ν©λλ€
     Daniellaκ³Ό Barryλ₯Ό λΉκ΅ν©λλ€
     Daniellaκ³Ό Chrisλ₯Ό λΉκ΅ν©λλ€
     Daniellaκ³Ό Ewaλ₯Ό λΉκ΅ν©λλ€
     ["Ewa", "Daniella", "Chris", "Barry", "Alex"]
     */
    ```
    
    ---
    
    ```swift
    // λ°°μ΄ μ λ ¬ μμ 
    let names = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]
    var defaultNames = names.sorted()
    print(defaultNames)
    
    // μ λ ¬ κΈ°μ€μ λ§λ€μ΄μ£Όλ ν¨μ λ§λ€κΈ°
    func backward(_ s1: String, _ s2: String) -> Bool {
    //    print("\(s1)κ³Ό \(s2)λ₯Ό λΉκ΅ν©λλ€")
        return s1 > s2
    }
    
    var reverseNames = names.sorted(by: backward)
    print(reverseNames)
    
    // μ μ­ν¨μ backwardμ λκ°μ΄ μλνλ ν΄λ‘μ  ννμμ λ§λ€μ΄
    // sortedμ by: λ§€κ°λ³μλ‘ μΈλΌμΈ ν΄λ‘μ λΌλ κ΅¬νλ²μΌλ‘ λ°λ‘ μ¨μ λ³΄λΈλ€
    reverseNames = names.sorted(by: { (_ s1: String, _ s2: String) -> Bool in
        return s1 > s2
    })
    print(reverseNames)
    
    // νμ€λ‘λ κ°λ₯
    reverseNames = names.sorted(by: { (_ s1: String, _ s2: String) -> Bool in return s1 > s2 })
    print(reverseNames)
    
    // λ μ§§κ²
    // λ°°μ΄μ΄ String λ¬Έμμ΄λ€λ‘ μ±μμ§ κ±Έ μλκΉ
    reverseNames = names.sorted(by: { (_ s1, _ s2) -> Bool in return s1 > s2 })
    print(reverseNames)
    
    // λ μ§§κ²
    reverseNames = names.sorted(by: { s1, s2 in return s1 > s2 })
    print(reverseNames)
    
    // λ μ§§κ²
    reverseNames = names.sorted(by: { s1, s2 in s1 > s2 })
    print(reverseNames)
    
    // μ§§μ μΈμμ΄λ¦μΌλ‘ λμ²΄νλ λ°©λ²λ μμ
    reverseNames = names.sorted(by: { $0 > $1 })
    print(reverseNames)
    
    // μ°μ°μ λ©μλ
    reverseNames = names.sorted(by: >)
    print(reverseNames)
    ```
    
    ## μΆλ ₯κ°
    
  ![Untitled - 2022-10-06T165400 888](https://user-images.githubusercontent.com/67450169/194249808-730c9b08-9a9c-4b09-aec2-c0225b6cdd4f.png)
    
    ---
    
    ## πΈμ€ν μμ
    
    ---
    
    ```swift
    // Arrayμ map λ§€μλ μμ 
    
    let digitNames: [Int: String] = [
        0: "Zero",
        1: "One",
        2: "Two",
        3: "Three",
        4: "Four",
        5: "Five",
        6: "Six",
        7: "Seven",
        8: "Eight",
        9: "Nine"
    ]
    
    let numbers: [Int] = [16, 58, 510]
    
    // ["OneSix", "FiveEight", "FiveOneZero"] λ°°μ΄ λ§λ€κΈ°
    let strings: [String] = numbers.map { (number: Int) -> String in
        // λ§€κ°λ³μλ‘ κ°μ Έμ¨ numberλ μμμ΄κΈ° λλ¬Έμ, λ³μλ‘ λ€μ λ§λ€μ΄μ€μΌ λ³κ²½ κ°λ₯νλ€ - μλμ° λ³μ
        var number: Int = number
        var output: String = ""
        
        repeat {
            // print("\(number % 10)")
            
            // number % 10 λ¬Έκ΅¬λ numberλ₯Ό 10μΌλ‘ λλ λλ¨Έμ§, κ·Έλ¬λκΉ μμ«μ  μ λ§¨ μλ«μλ¦¬μ νμλ¦¬
            // μμλ¦¬μ ν΄λΉνλ λ¬Έμμ΄μ κ³μ μμ λν΄μ£Όλ λ¬Έμμ΄ κ²°ν©
            output = digitNames[number % 10]! + output
            
            // numberλ Intμ΄κΈ° λλ¬Έμ, 10μΌλ‘ λλλ©΄ μμ«μ  μ΄νμ κ°μ λ΄λ¦Όμ²λ¦¬νλ€.
            number /= 10
        } while number > 0
        
        return output
    }
    
    print("\(strings)")
    ```
    
    ---
    
    ## πΈ!μ²λ¦¬ νΌνκΈ° & μ΅μλ λ°μΈλ© λ€λ₯Έ λ°©λ²
    
    ```swift
    // Arrayμ map λ§€μλ μμ 
    
    let digitNames: [Int: String] = [
        0: "Zero",
        1: "One",
        2: "Two",
        3: "Three",
        4: "Four",
        5: "Five",
        6: "Six",
        7: "Seven",
        8: "Eight",
        9: "Nine"
    ]
    
    let numbers: [Int] = [16, 58, 510]
    
    // ["OneSix", "FiveEight", "FiveOneZero"] λ°°μ΄ λ§λ€κΈ°
    let strings: [String] = numbers.map { (number: Int) -> String in
        // λ§€κ°λ³μλ‘ κ°μ Έμ¨ numberλ μμμ΄κΈ° λλ¬Έμ, λ³μλ‘ λ€μ λ§λ€μ΄μ€μΌ λ³κ²½ κ°λ₯νλ€ - μλμ° λ³μ
        var number: Int = number
        var output: String = ""
        
        repeat {
            // print("\(number % 10)")
            
            // number % 10 λ¬Έκ΅¬λ numberλ₯Ό 10μΌλ‘ λλ λλ¨Έμ§, κ·Έλ¬λκΉ μμ«μ  μ λ§¨ μλ«μλ¦¬μ νμλ¦¬
            // μμλ¦¬μ ν΄λΉνλ λ¬Έμμ΄μ κ³μ μμ λν΄μ£Όλ λ¬Έμμ΄ κ²°ν©
            // output = digitNames[number % 10]! + output
            
            // !μ²λ¦¬λ νΌνκ³  μΆμ΄μ
            /*
            if let name = digitNames[number % 10] {
                output = name + output
            } else {
                output = "?" + output
            }
            */
            
            // μ§§κ² μ°λ μ΅μλ λ°μΈλ©μ λ λ€λ₯Έ λ°©λ²
            let name = digitNames[number % 10] ?? "?"
            output = name + output
            
            // numberλ Intμ΄κΈ° λλ¬Έμ, 10μΌλ‘ λλλ©΄ μμ«μ  μ΄νμ κ°μ λ΄λ¦Όμ²λ¦¬νλ€.
            number /= 10
        } while number > 0
        
        return output
    }
    
    print("\(strings)")
    ```
    
    ---
    
    ## πΈμΊ‘μ³κ°
    
    ---
    
    ```swift
    // μΊ‘μ²κ° μμ 
    func makeIncrementer(forIncrement amount: Int) -> () -> Int {
        var runningTotal: Int = 0
        
        func incrementer() -> Int {
            runningTotal += amount
            return runningTotal
        }
        
        return incrementer
    }
    
    let increFunc = makeIncrementer(forIncrement: 10)
    
    print("\(increFunc())") // 10
    print("\(increFunc())") // 10 + 10 = 20
    print("\(increFunc())") // 20 + 10 = 30
    ```
    
    ---
    
    ```swift
    // μΊ‘μ²κ° & μ°Έμ‘° νμ μμ 
    
    func makeIncrementer(forIncrement amount: Int) -> () -> Int {
        var runningTotal: Int = 0
        
        func incrementer() -> Int {
            runningTotal += amount
            return runningTotal
        }
        
        return incrementer
    }
    
    // μμ±λ λ°νλλ ν¨μλ runningTotal = 0,amount = 10μΌλ‘ μΊ‘μ³λμ΄ μλ
    let increFuncTen = makeIncrementer(forIncrement: 10)
    
    // μμ±λ λ°νλλ ν¨μλ runningTotal = 0,amount = 7λ‘ μΊ‘μ³λμ΄ μλ
    let increFuncSeven = makeIncrementer(forIncrement: 7)
    
    print("\(increFuncTen())") // 0 + 10 = 10
    print("\(increFuncSeven())") // 0 + 7 = 7
    
    print("\(increFuncTen())") // 10 + 10 = 20
    print("\(increFuncSeven())") // 7 + 7 = 14
    
    print("\(increFuncTen())") // 20 + 10 = 30
    print("\(increFuncSeven())") // 14 + 7 = 21
    
    // λ ν¨μμ κ΄κ³λ μ°Έμ‘° νμμ΄λΌλ κ±Έ μμλ³΄λ € νλ€.
    // λμΌν runningTotal κ°μ κ³΅μ νκ³  μλ€.
    let alsoIncreFuncTen = increFuncTen
    
    print("\(increFuncTen())") // 30 + 10 = 40
    print("\(alsoIncreFuncTen())") // 0 + 10 = 10 ? -> μ€μ λ‘λ 50
    print("\(increFuncTen())") // 40 + 10 = 50 ? -> μ€μ λ‘λ 60
    
    // νμνλ©΄ μλ‘ λ§λ€μ΄μΌ...
    let myIncreFuncTen = makeIncrementer(forIncrement: 10)
    print("\(myIncreFuncTen())") // 0 + 10 = 1
    ```
    
    ---
    
    ## πΈμ΄μ€μΌμ΄ν ν΄λ‘μ 
    
    ---
    
    ```swift
    var completionHandlers: [() -> Void] = []
    
    func someFunctionWithEscapingClosures(completionHandler: @escaping () -> Void ){
        completionHandlers.append(completionHandler)
    }
    
    func someFunctionWithNoneEscapingClosures(closure: () -> Void){
        closure()
    }
    
    class SomeClass{
        var x = 0 
        func doSomething(){
            someFunctionWithEscapingClosures(completionHandler:{() -> Void in
                print("hello")
                self.x = 100
            })
            someFunctionWithNoneEscapingClosures{() -> Void in 
                print("world")
                x = 200
            }
        }
    }
    let instance = SomeClass()
    instance.doSomething()
    print("None x:\(instance.x)")
    
    if let completionHandler = completionHandlers.first{
        completionHandler()
        print("x:\(instance.x)")
    }
    ```
    
    ## closer κ°μ§κ³  λ§€κ°λ³μλ₯Ό μ¬μ©ν λ escaping μ¬μ©!!
    
    ---
    
    ## πΈmutatingμ μμλ³΄μ!!
    
    ```swift
    // mutatingμ μμλ³΄μ
    
    class SomeClass {
        var name: String = ""
        
        func changeName(newName: String) {
            self.name = newName
        }
    }
    
    var someThingByClass = SomeClass()
    someThingByClass.changeName(newName: "ned")
    print("someThingByClass.name = \(someThingByClass.name)")
    
    struct SomeStruct {
        var name: String = ""
        
        // μ΄ λ©μλμ μν΄μ νλ‘νΌν°κ° λ°λ μ μμμ μλ¦¬κΈ° μν΄ mutatingμ μμ λΆμΈλ€
        mutating func changeName(newName: String) {
            self.name = newName
        }
    }
    
    var someThingByStruct = SomeStruct()
    someThingByStruct.changeName(newName: "λ½λ½λ‘")
    print("someThingByStruct.name = \(someThingByStruct.name)")
    ```
    
    ---
    
   ![Untitled - 2022-10-06T165424 615](https://user-images.githubusercontent.com/67450169/194249852-da40029c-8735-4926-8d8f-1e221e29207f.png)
    
   ![Untitled - 2022-10-06T165425 565](https://user-images.githubusercontent.com/67450169/194249873-60a30c43-458b-4535-85c6-08d3e63c259f.png)
    ---
    
    ![Untitled - 2022-10-06T165427 977](https://user-images.githubusercontent.com/67450169/194249902-d824e069-d8ae-4fa4-867e-248e73189e05.png)
    
    ---
    
   ![Untitled - 2022-10-06T165428 988](https://user-images.githubusercontent.com/67450169/194249924-056f02d6-1b97-4c91-af3d-819e3566f0b1.png)
    
    ---
    
    ## πΈ@escaping closure κ°λ
    
    ν΄λ‘μ κ° ν¨μλ‘λΆν° escape νλ€λ κ²μ ν΄λΉ ν¨μμ μΈμλ‘ ν΄λ‘μ κ° μ λ¬λμ§λ§, **ν¨μκ° λ°νλν μ€ν** λλκ²μ μλ―Ένλ€. ν¨μμ μΈμκ° ν¨μμ μμ­μ νμΆνμ¬ ν¨μ λ°μμ μ¬μ©ν  μ μλ κ°λμ κΈ°μ‘΄μ μ°λ¦¬κ° μκ³  μλ λ³μμ `scope` κ°λμ λ¬΄μνλ€. 
    
    μ? ν¨μμ μ μΈλ λ‘μ»¬ λ³μκ° λ‘μ»¬ λ³μμ μμ­μ λ°μ΄λμ΄ **ν¨μ λ°**μμλ μ ν¨νκΈ° λλ¬Έμ΄λ€.
    
    ---
    
    ```swift
    // ν¨μ μΈλΆμ ν΄λ‘μ λ₯Ό μ μ₯νλ μμ
    // ν΄λ‘μ λ₯Ό μ μ₯νλ λ°°μ΄
    var completionHandlers: [() -> Void] = []
    
    func withEscaping(completion: @escaping () -> Void) {
        // ν¨μ λ°μ μλ completionHandlers λ°°μ΄μ ν΄λΉ ν΄λ‘μ λ₯Ό μ μ₯
        completionHandlers.append(completion)
    }
    
    func withoutEscaping(completion: () -> Void) {
        completion()
    }
    
    class MyClass {
        var x = 10
        func callFunc() {
            withEscaping { self.x = 100 }
            withoutEscaping { x = 200 }
        }
    }
    let mc = MyClass()
    mc.callFunc()
    print(mc.x)
    completionHandlers.first?()
    print(mc.x)
    
    // κ²°κ³Ό
    // 200
    // 100
    ```
    
    μμ μμμμλ MyClassμ ν¨μΒ `callFunc()`λ ν΄λ‘μ λ₯Ό μΈμλ₯Ό κ°λΒ `withEscaping(completion:)`
    κ³ΌΒ `withoutEscaping(completion:)`μ κ°κ° νΈμΆνλ€. μ΄ λΒ `withEscaping(completion:)`
    μΒ `completion`μ νλΌλ―Έν°κ°Β `Escaping Closure`ννλ‘ κ΅¬νλμ΄ μλ€.
    
    Β `completionHandlers.append(completion)`μ½λλ₯Ό ν΅ν΄Β `withEscaping(completion:)`
    μΈλΆμ ν΄λ‘μ λ₯Ό μ μ₯νλ€. 
    
    μ¦, ν΄λ‘μ κ° ν¨μμμ λΉ μ Έλκ°λ€. μ΄λ κ² ν¨μλ₯Ό νΈμΆνλ λμ€μ ν΄λΉ ν¨μ μΈλΆμ ν΄λ‘μ λ₯Ό μ μ₯νκΈ° μν΄μλ ν΄λ‘μ λΒ `Escaping Closure`μ΄μ΄μΌ νλ€.
    
    **μ΄ λ, ν΄λ‘μ κ° νμΆνλ€λ μλ―Έλ ν΄λΉ ν¨μμ μ€νμ μ€κ°μ λκ³ , νμΆ(escape)νλ μλ―Έκ° μλλ€. μ¬κΈ°μμ νμΆ(escape)μ ν΄λ‘μ λ₯Ό μΈλΆλ‘ λ³΄λΌ μ μλ€λ μλ―Έμ΄λ€.**
    
    ---
    
    ## πΈ@escaping μΈμ  μ¬μ©νλκ°
    
    ```swift
    func ex1(completion:() -> ()) {
    	completion()
    }
    ```
    
    ### completion == λ§€κ°λ³μ X , return  X μΈ () β () ν¨μ νμ
    
    ### Swift closures λ 1κΈ κ°μ²΄μ΄κΈ°μ νλΌλ―Έν°λ‘ closuresλ₯Ό λ°μ μ μλ€!
    
    - 1κΈκ°μ²΄
        1. λ³μμ μ μ₯ν μ μλ€.
        2. λ§€κ°λ³μλ‘ μ λ¬ν  μ μλ€.
        3. return κ°μΌλ‘ μ¬μ©ν  μ μλ€.
    - νλΌλ―Έν° μΈμκ° κ°λ₯
    - λ³μ & μμ λμ κ°λ₯
    
    ---
    
    ```swift
    ex1{
    		print("closures study")                          //closures study
    }
    ```
    
     
    
    ### λ§€κ°λ³μλ‘ ν¨μλ₯Ό λκ²¨μ€ μ μκ³ 
    
    **λ§€κ°λ³μλ‘ λκ²¨μ€ ν¨μκ° ex1 ν¨μ λ΄λΆμμ completionμ΄λ λ§€κ° μμλ‘ μ μ₯λμ΄ μ¬μ©λλ€.**
    
    ```swift
    func ex1(completion: () -> ()) {
        DispatchQueue.main.asyncAfter(deadline: .now() + 3) { //λΉλκΈ° 3μ΄ λλ μ΄
            completion()
        }
    }
    ```
    
    λ§€κ°λ³μλ‘ λ°μ completionμ μ μ₯λ ν΄λ‘μ λ₯Ό 3μ΄νμ μ€ν μν€κ³  μΆλ€? 
    
    μ΄λ κ² μ½λ©ν  κ²½μ° β> **Error λ°μ**
    
    μΌλ°μ μΌλ‘ **μλ¬΄λ° ν€μλ μμ΄ νλΌλ―Έν°λ‘ λ°λ ν΄λ‘μ **λ λͺ¨λ **non-escaping closure**μ΄λ€.
    
    μ΄λ¦ κ·Έλλ‘ νμΆμ΄ λΆκ°λ₯ν ν΄λ‘μ 
    
    ν¨μμ νλ¦μ νμΆνμ§ μλ ν΄λ‘μ λ λ»μΌλ‘, ν¨μκ° μ’λ£λκ³  λμ ν΄λ‘μ κ° μ€νλ  μ μλ€λ λ§μ΄λ€. ν¨μκ° μ’λ£λ λ ν΄λ‘μ μ μ¬μ©λ κ°μ΄ μ’λ£λμ΄μ κ°μ΄ λλμΌ λλκ²μ΄λ€.
    
    -κ·Όλ° μ ν¨μ κ°μ κ²½μ°λ **asnycλ‘ 3μ΄λ€μ ν΄λ‘μ λ₯Ό μ€ν**λκ²λ ν΄λ²λ Έλ€. 
    
    ```swift
    func ex1(completion: () -> ()) {
    	print("start")
      DispatchQueue.main.asyncAfter(deadline: .now() + 3) { //λΉλκΈ° 3μ΄ λλ μ΄
    	print("when???")
    }
    print("the end")
    }
    
    ex1{}
    print("really the end")
    
    ```
    
    - κ²°κ³Ό
        
        ```swift
        //start
        //the end
        //really the end
        //when???
        ```
        
    
    ν¨μ λ΄λΆμμ **3μ΄ λ€μ μ€νλλ async task**λ₯Ό μ€λ²λ ΈκΈ° λλ¬Έμ μ΄λ‘ μ **ν¨μμ μμ μ£ΌκΈ°κ° μμ ν λλλ²λ Έμ§λ§, κ·Έ μ΄νμ ν΄λΉ μμμ΄ μ€ν**λκ² λλ€.
    
    μ΄κ²μ΄ **ν¨μμ νλ¦μ νμΆν μν©**μΈλ°, 
    
    3μ΄λ€μ μ€νλλ async taskλ₯Ό completionμΌλ‘ λ€μ λ°κΎΌλ€ μκ°ν΄λ³΄λ©΄ **completionμ ν¨μκ° λλκΈ° μ μ μ€νμ΄ λͺ¨λ μ’λ£λμ΄μΌ νλλ°,** **ν¨μμ νλ¦μ λ²μ΄λ νΈμΆλμ΄μΌ νκΈ° λλ¬Έμ μ΄λ non-escaping parameter μλκΈ° λλ¬Έμ** μλ¬κ° μκΈ΄λ€.
    
                                                        **λ°λΌμ  non-escapingμ κ²½μ°**
    
    1. ν¨μ λ΄λΆμμ μ§μ  μ€ννκΈ° μν΄μλ§ μ¬μ©νλ€.
    2. νλΌλ―Έν°λ‘ λ°μ ν΄λ‘μ λ λ³μ & μμμ λμ ν  μ μκ³ 
    3. μ€μ²© ν¨μ λ΄λΆμμ ν΄λ‘μ λ₯Ό μ¬μ©ν  κ²½μ°, μ€μ²©ν¨μλ₯Ό λ¦¬ν΄ν  μ μλ€.
    4. ν¨μμ μ€ν νλ¦μ νμΆνμ§ μμ, ν¨μκ° μ’λ£λκΈ° μ μ λ¬΄μ‘°κ±΄ μ€νλμ΄μΌνλ€.
    
    μ΄ 4κ°μ§ νΉμ§μ κ°μ§κ³  μλ€.
    
    κ·Έλ λ€λ©΄ parameterλ‘ λ°μ closureλ **λΉλκΈ°λ‘ μ¬μ©λͺ»νλ?** **ν¨μ νλ¦ νμΆ λͺ»νλ?** ν λ μ¬μ©νλ ν€μλκ°  **@escaping** μ΄λ€.
    
    ```swift
    func ex1(completion: @escaping () -> ()) {
        DispatchQueue.main.asyncAfter(deadline: .now() + 3) {
            completion()
        }
    }
    ```
    
    μ΄λ° μμΌλ‘ ν¨μμ νμ μ μΈνκΈ° μ μ @escapingμ΄λ ν€μλλ₯Ό λΆμ¬μ£Όλ©΄, 
    
    μ΄ ν΄λ‘μ λ ν¨μμ μ€ν νλ¦μ μκ΄μμ΄ μ€νλλ ν΄λ‘μ λ€ λΌκ³  μλ €μ£Όλ κ²μ΄λ€.
    
    ```swift
    func ex1(completion: @escaping () -> ()) {
        DispatchQueue.main.asyncAfter(deadline: .now() + 3) {
            completion()
        }
    }
    
    ex1{
    	print("running now")
    }
    print("func the end")
    ```
    
    μ€νν΄λ³΄λ©΄ μλ¬ μμ΄ `completion`μ΄ μ μ€νλλ€.
    
    `func the end`κ° λ¨Όμ  μ€νλκ³ , 3μ΄ λ€μ `running now`κ° μ€νλ  κ²μ΄λ€. 
    
    μ΄κ²μ΄ **@escaping** μ΄λ€.
    
    ---
    
    ## πΈClosure?, Closure capture?
    
    Closureλ λ΄λΆ ν¨μμ λ΄λΆ ν¨μμ μν₯μ λ―ΈμΉλ μ£Όλ³ νκ²½μ λͺ¨λ ν¬ν¨ν κ°μ²΄μ΄λ€.
    
    ```swift
    funcd doSomething(){
    	var message = "hi i'm wonhyeong"
    //ν΄λ‘μ  λ²μ μμ
    
    var num = 10  //closure κΈ°μ€ μΈλΆ λ³μ(num)
    let closure = { print(num)}
    
    //ν΄λ‘μ  λ²μ λ
    
    print(message)
    }
    ```
    
    closureλ λ΄λΆμμ **μΈλΆ λ³μμΈ numμ΄λΌλ Value νμμ λ³μλ₯Ό μ¬μ©**νκΈ° λλ¬Έμ n**umμ κ°μ λ΄λΆμ μΌλ‘ μ μ₯**νκ³  μλλ° μ΄κ²μ **numμ κ°μ΄ capture λμλ€** λΌκ³  νννλ€.
    
    messageλ λ³μλ closure λ΄λΆμμ μ¬μ©νμ§ μκΈ° λλ¬Έμ λ°λ‘ μ μ₯(μΊ‘μ³)νμ§ μμλ€.
    
    ## πΈClosureμ μΊ‘μ³ λ°©μ
    
    ### closureλ κ°μ μΊ‘μ³ν λ Value/Reference νμμ κ΄κ³μμ΄ Reference Capture νλ€.
    
    ```swift
    func doSomething(){
    	var num: Int = 0
    	print("1 = \(num)")
    
    	let closure = {
    		print("3 = \(num)")
    }
    
    num = 100
    print("2 = \(num)")
    closure()
    }
    ```
    
    closureλ κ°μ Scopeμ μ§μ­λ³μμΈ numμ μ¬μ©νλ―λ‘ closureλ numκ°μ μΊ‘μ³ν  κ²μ΄λ€.
    
    κ·Όλ° numμ΄ Intν, Value Typeμ΄μ¬λ **Reference Caputure**λ₯Ό νλ€!!
    
    ---
    
    λ°λΌμ  closureλ₯Ό μ€ννκΈ° μ μ numμ κ°μ λ°κΎΈλ©΄, closureλ numμ μ°Έμ‘°νκ³  μκΈ° λλ¬Έμ closureμμ μ€ννλ numμ κ°λ λ°λλ€.
    
    ### closureμ λ³μκ° μ¬μ©λλ μμ μ λ³μμ κ°μ νκ°νλ€.
    
    - νλ‘κ·Έλ¨ κ²°κ³Ό
