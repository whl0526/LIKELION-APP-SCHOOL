![Untitled](https://user-images.githubusercontent.com/67450169/195075844-1d5ed9b2-d12e-481f-b55e-f18b9214a9a7.png)
## ๐ธ๊ตฌ์กฐ์ฒด ์ ์

๊ตฌ์กฐ์ฒด ๋ฉค๋ฒ ์ ๊ทผ 

```objectivec
//
//  main.m
//  HelloObjC
//
//  Created by ์ด์ํ on 2022/10/11.
//

#import <Foundation/Foundation.h>

struct Books{
    NSString *title;
    NSString *author;
    NSString *subject;
    int bookId;
    
};

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        struct Books book1;
        struct Books book2;
        
        book1.title = @"C์ธ์ด ํ๋ก๊ทธ๋๋ฐ";
        book1.author = @"๋ฐ๋์ค ๋ฆฌ์น";
        book1.subject = @"c์ธ์ด ํ์ต ๊ณต์๋์";
        book1.bookId = 1234567;
        
        NSLog(@"%@",book1.title);
        NSLog(@"%@",book1.author);
        NSLog(@"%@",book1.subject);
        NSLog(@"%@",book1.bookId);
        
        
        
        
            }
    return 0;
}
```

ํจ์์ ์ธ์๋ก์์ ๊ตฌ์กฐ์ฒด

```objectivec
//
//  main.m
//  HelloObjC
//
//  Created by ์ด์ํ on 2022/10/11.
//

#import <Foundation/Foundation.h>

struct Books{
    NSString *title;
    NSString *author;
    NSString *subject;
    int bookId;
    
};

@interface SampleClass : NSObject
-(void)printBookinfo:(struct Books)book;
@end

@implementation SampleClass
-(void)printBookinfo:(struct Books)book;{
    NSLog(@"%@", book.title);
    NSLog(@"%@", book.author);
    NSLog(@"%@", book.subject);
    NSLog(@"%d", book.bookId);
}

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        struct Books book1;
       // struct Books book2;
        
        book1.title = @"C์ธ์ด ํ๋ก๊ทธ๋๋ฐ";
        book1.author = @"๋ฐ๋์ค ๋ฆฌ์น";
        book1.subject = @"c์ธ์ด ํ์ต ๊ณต์๋์";
        book1.bookId = 1234567;
        
//        NSLog(@"%@",book1.title);
//        NSLog(@"%@",book1.author);
//        NSLog(@"%@",book1.subject);
//        NSLog(@"%d",book1.bookId);
        
        SampleClass *sampleClass = [[SampleClass alloc]init];
        [sampleClass printBookinfo:book1];
        
        
            }
    return 0;
}
```

---

## ๐ธโโโ๊ตฌ์กฐ์ฒด์ ๋ํ ํฌ์ธํฐ โโโ

```objectivec
#import <Foundation/Foundation.h>

struct Books {
    NSString *title;
    NSString *author;
    NSString *subject;
    int bookId;
};

@interface SampleClass : NSObject
- (void)updateBookInfoTitle:(struct Books)books;
- (void)printBookInfo:(struct Books)books;

- (void)updateBookTitle:(struct Books *)book;
- (void)descriptionBookInfo:(struct Books *)book;
@end

@implementation SampleClass

- (void)updateBookInfoTitle:(struct Books)books {
    books.title = @"Hello World";
}

- (void)printBookInfo:(struct Books)books {
    NSLog(@"%@", books.title);
    NSLog(@"%@", books.author);
    NSLog(@"%@", books.subject);
    NSLog(@"%d", books.bookId);
}

- (void)updateBookTitle:(struct Books *)books {
    books->title = @"Hello Objective-C";
}

- (void)descriptionBookInfo:(struct Books *)books {
    NSLog(@"%@", books->title);
    NSLog(@"%@", books->author);
    NSLog(@"%@", books->subject);
    NSLog(@"%d", books->bookId);
}

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        struct Books book1;
        
        book1.title = @"C์ธ์ด ํ๋ก๊ทธ๋๋ฐ";
        book1.author = @"๋ฐ๋์ค ๋ฆฌ์น";
        book1.subject = @"C์ธ์ด ํ์ต ๊ณต์๋์";
        book1.bookId = 1234567;
        
        SampleClass *sampleClass = [[SampleClass alloc] init];
        
        // ๊ฐ์ผ๋ก ๋ณต์ ์ํฌ ๋งค๊ฐ๋ณ์ - call by value
        [sampleClass updateBookInfoTitle:book1];
        [sampleClass printBookInfo:book1];
        
        // ํฌ์ธํฐ ์ฐธ์กฐ๊ฐ์ผ๋ก ์๋ ค์ฃผ๊ณ  ์ง์  ๊ฑด๋๋ฆฌ๊ฒ ํ  ๋งค๊ฐ๋ณ์ - call by reference
        [sampleClass updateBookTitle:&book1];
        [sampleClass descriptionBookInfo:&book1];
    }
    return 0;
}
```

---

## ๐ธtypedef

```objectivec
#import <Foundation/Foundation.h>

/*
struct Books {
    NSString *title;
    NSString *author;
    NSString *subject;
    int bookId;
};

typedef struct Books BOOK;
 
์ด๋ ๊ฒ ๋๋ ์ ์ธ ๊ฑธ ํ๋ฒ์ ์ฐ์๋ฉด...
*/
typedef struct Books {
    NSString *title;
    NSString *author;
    NSString *subject;
    int bookId;
} BOOK;

@interface SampleClass : NSObject
- (void)updateBookInfoTitle:(BOOK)books;
- (void)printBookInfo:(BOOK)books;

- (void)updateBookTitle:(BOOK *)book;
- (void)descriptionBookInfo:(BOOK *)book;
@end

@implementation SampleClass

- (void)updateBookInfoTitle:(BOOK)books {
    books.title = @"Hello World";
}

- (void)printBookInfo:(BOOK)books {
    NSLog(@"%@", books.title);
    NSLog(@"%@", books.author);
    NSLog(@"%@", books.subject);
    NSLog(@"%d", books.bookId);
}

- (void)updateBookTitle:(BOOK *)books {
    books->title = @"Hello Objective-C";
}

- (void)descriptionBookInfo:(BOOK *)books {
    NSLog(@"%@", books->title);
    NSLog(@"%@", books->author);
    NSLog(@"%@", books->subject);
    NSLog(@"%d", books->bookId);
}

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        BOOK book1;
        
        book1.title = @"C์ธ์ด ํ๋ก๊ทธ๋๋ฐ";
        book1.author = @"๋ฐ๋์ค ๋ฆฌ์น";
        book1.subject = @"C์ธ์ด ํ์ต ๊ณต์๋์";
        book1.bookId = 1234567;
        
        SampleClass *sampleClass = [[SampleClass alloc] init];
        
        // ๊ฐ์ผ๋ก ๋ณต์ ์ํฌ ๋งค๊ฐ๋ณ์ - call by value
        [sampleClass updateBookInfoTitle:book1];
        [sampleClass printBookInfo:book1];
        
        // ํฌ์ธํฐ ์ฐธ์กฐ๊ฐ์ผ๋ก ์๋ ค์ฃผ๊ณ  ์ง์  ๊ฑด๋๋ฆฌ๊ฒ ํ  ๋งค๊ฐ๋ณ์ - call by reference
        [sampleClass updateBookTitle:&book1];
        [sampleClass descriptionBookInfo:&book1];
    }
    return 0;
}
```

## ๐ธtypedef์ ๊ตฌ์กฐ์ฒด

```objectivec
#import <Foundation/Foundation.h>

// Person ๊ตฌ์กฐ์ฒด๋ฅผ ์ ์ํด์ ํ์์ด๋ฆ์ผ๋ก ์ฐ๊ณ  ์ถ๋ค๋ฉด
typedef struct _Person {
    float height;
    int weight;
} Person;

// BMI ๊ณ์ฐ ํจ์
float calcBMI(Person person) {
    return person.weight / (person.height * person.height);
}

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        //struct _Person person;
        Person person;
        
        person.height = 1.65;
        person.weight = 55;
        
        
        NSLog(@"height : %f", person.height);
        NSLog(@"weight : %d", person.weight);
        NSLog(@"BMI : %f", calcBMI(person));
    }
    return 0;
}
```

## ๐ธํ์์บ์คํ

```objectivec
#import <Foundation/Foundation.h>

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        int sum = 17;
        int count = 5;
        
        // int์ int์ ๋๋์์ด๋ผ int๋ผ๊ณ  ๊ฒฐ๊ณผ๋ฅผ ์๊ฐํ  ์ ์์
        NSLog(@"Value of mean : %d", (sum / count));
        
        // ๊ฐ์ ๋ก ์ ๊ณ์ฐ ๊ฒฐ๊ณผ๋ฅผ float๊ฐ์ผ๋ก ๊ฐ๊ฐ ํ์์บ์คํ ๋ณํ์ฒ๋ฆฌํด์ค๋ค๋ฉด? ๊ฒฐ๊ณผ๋ float ํ์์ด ๋๋ค.
        NSLog(@"Value of mean : %f", ((float)sum / (float)count));
    }
    return 0;
}
```

---

## ๐ธํด๋์ค์ ๊ฐ์ฒด

๋ฐ์ดํฐ ๋ฉค๋ฒ ์ก์ธ์ค

```objectivec
#import <Foundation/Foundation.h>

@interface Box : NSObject {
    double length;  // ๊ธธ์ด
    double breadth; // ํญ
    double height;  // ๋์ด
}
//@property(nonatomic, readwrite) double length;
//@property(nonatomic, readwrite) double breadth;
@property(nonatomic, readwrite) double height;

- (double)volume;

@end

@implementation Box

// ์ ์ธ๋ ํ๋กํผํฐ๋ฅผ ๊ฐ์ฅ ์ฝ๊ฒ ๊ตฌํ๋ถ์์ ๋ง๋ค์ด์ฃผ๋ ๋ฐฉ๋ฒ
//@synthesize length;
//@synthesize breadth;
@synthesize height;

// ์ด๊ธฐํ ์ฒ๋ฆฌํ ๋ฐํ๋  ์ธ์คํด์ค๋ id๋ผ๊ณ  ํต์นญ๋๋ค.
- (id)init {
    self = [super init];
    self->length = 1.0;
    self->breadth = 1.0;
    return self;
}

- (double)volume {
    return length * breadth * height;
}

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        Box *box1 = [[Box alloc] init];
        Box *box2 = [[Box alloc] init];
        
        box1.height = 5.0;
        box2.height = 10.0;
        
        NSLog(@"Volume of Box1 : %f", [box1 volume]);
        NSLog(@"Volume of Box2 : %f", [box2 volume]);
    }
    return 0;
}
```

## ๐ธ์์

```objectivec
#import <Foundation/Foundation.h>

// Person ํด๋์ค ์ ์
@interface Person : NSObject {
    NSString *personName;
    NSInteger personAge;
}

- (id)initWithName:(NSString *)name andAge:(NSInteger)age;
- (void)print;
@end

@implementation Person

- (id)initWithName:(NSString *)name andAge:(NSInteger)age {
    self = [super init];
    
    personName = name;
    personAge = age;
    
    return self;
}

- (void)print {
    NSLog(@"Name: %@", personName);
    NSLog(@"Age: %ld", personAge);
}

@end

// Person์ ์์๋ฐ์ Employee ํด๋์ค ์ ์
@interface Employee : Person {
    NSString *employeeEducation;
}

- (id)initWithName:(NSString *)name andAge:(NSInteger)age andEducation:(NSString *)education;
- (void)print;

@end

@implementation Employee

- (id)initWithName:(NSString *)name andAge:(NSInteger)age andEducation:(NSString *)education {
    self = [super initWithName:name andAge:age];
    employeeEducation = education;
    return self;
}

- (void)print {
    [super print];
    NSLog(@"Educaiton: %@", employeeEducation);
}

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {

        Person *person = [[Person alloc] initWithName:@"Ned" andAge:13];
        [person print];
        
        Employee *employee = [[Employee alloc] initWithName:@"ํ๊ธธ๋" andAge:15 andEducation:@"์๋น"];
        [employee print];
    }
    return 0;
}
```

## ๐ธActivity ์์ Obj-C๋ฅผ Swift๋ก ๋ฐ๊พธ์ด ๋ณด์!@#!@#

```swift
import Foundation
class Person {
    var personName: String = ""
    var personAge: Int = 0
    
    init(name: String, age: Int) {
        self.personName = name
        self.personAge = age
    }
    func Info() {
        print("์ด๋ฆ \(personName)")
        print("๋์ด \(personAge)")
    }
}

class Employee : Person {
    var employeeEdu: String = ""
    
    init(name: String, age: Int, education: String) {
        super.init(name: name, age: age)
        self.employeeEdu = education
    }
    
    override func Info() {
        super.Info()
        print("๊ต์ก : \(employeeEdu)")
    }
    
}
var person: Person = Person(name: "wh1", age: 1)
var employee : Employee = Employee(name: "wh2", age: 2, education: "dev")
person.Info();
employee.Info();
```

## ๐ธ๋คํ์ฑ Obj-C

```objectivec
#import <Foundation/Foundation.h>

// ์ค๊ณฝ ํด๋์ค ์ ์
@interface Shape : NSObject {
    CGFloat area;   // ๋์ด
}

- (void)printArea;
- (void)calculateArea;
@end

@implementation Shape

- (void)printArea {
    NSLog(@"The area is %f", area);
}

- (void)calculateArea {
    // ์์ง ๋ชจ๋ฅด๊ฒ ์
}

@end

// ์ค๊ณฝ์ ์์๋ฐ์ ์ ์ฌ๊ฐํ ํด๋์ค ์ ์
@interface Square : Shape {
    CGFloat length; // ์ ์ฌ๊ฐํ ๋ณ์ ๊ธธ์ด
}

- (id)initWithSide:(CGFloat)side;
- (void)calculateArea;
@end

@implementation Square

- (id)initWithSide:(CGFloat)side {
    self = [super init];
    length = side;
    return self;
}

- (void)calculateArea {
    area = length * length;
}

@end

// ์ค๊ณฝ์ ์์๋ฐ์ ์ง์ฌ๊ฐํ ํด๋์ค ์ ์
@interface Rectangle : Shape

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        Shape *shape = [[Shape alloc] init];
        [shape printArea];
        
        Square *square = [[Square alloc] initWithSide:10.0];
        [square calculateArea];
        [square printArea];
    }
    return 0;
}
```

## ๐ธ์์ ์ฝ๋ cacultate, Rectangle ์ถ๊ฐ

```objectivec
#import <Foundation/Foundation.h>

// ์ค๊ณฝ ํด๋์ค ์ ์
@interface Shape : NSObject {
    CGFloat area;   // ๋์ด
}

- (void)printArea;
- (void)calculateArea;
@end

@implementation Shape
- (void)printArea {
    NSLog(@"The area is %f", area);
}

- (void)calculateArea {
    // ์์ง ๋ชจ๋ฅด๊ฒ ์
}
@end

// ์ค๊ณฝ์ ์์๋ฐ์ ์ ์ฌ๊ฐํ ํด๋์ค ์ ์
@interface Square : Shape {
    CGFloat length; // ์ ์ฌ๊ฐํ ๋ณ์ ๊ธธ์ด
}

- (id)initWithSide:(CGFloat)side;
- (void)calculateArea;
@end

@implementation Square
- (id)initWithSide:(CGFloat)side {
    self = [super init];
    length = side;
    return self;
}

- (void)calculateArea {
    area = length * length;
}
@end

// ์ค๊ณฝ์ ์์๋ฐ์ ์ง์ฌ๊ฐํ ํด๋์ค ์ ์
@interface Rectangle : Shape {
    CGFloat length;
    CGFloat breadth;
}

- (id)initWithLength:(CGFloat)length andBreadth:(CGFloat)breadth;
@end

@implementation Rectangle
- (id)initWithLength:(CGFloat)length andBreadth:(CGFloat)breadth {
    self = [super init];
    self->length = length;
    self->breadth = breadth;
    return self;
}

- (void)calculateArea {
    area = length * breadth;
}
@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        Shape *shape = [[Shape alloc] init];
        [shape printArea];
        
        Square *square = [[Square alloc] initWithSide:10.0];
        [square calculateArea];
        [square printArea];
        
        Rectangle *rectangle = [[Rectangle alloc] initWithLength:10.0 andBreadth:5.0];
        [rectangle calculateArea];
        [rectangle printArea];
    }
    return 0;
}
```

## ๐ธ์์ ์ฝ๋ Obj-C ์์ Swift๋ก ๋ฐ๊พธ์ด๋ณด์!@#$%%

๊ฐ์ฌ๋ ์ฝ๋

```swift
class Shape {
    var area: CGFloat = 0.0
    
    func printArea() {
        print("The area is \(area)")
    }
    
    func calculateArea() {
        // ์์ง ๋ชจ๋ฅด๊ฒ ์
    }
}

class Square: Shape {
    var length: CGFloat = 0.0
    
    init(side: CGFloat) {
        super.init()
        length = side
    }
    
    override func calculateArea() {
        super.calculateArea()
        area = length * length
    }
}

class Rectangle: Shape {
    var length: CGFloat = 0.0
    var breadth: CGFloat = 0.0
    
    init(length: CGFloat, breadth: CGFloat) {
        super.init()
        self.length = length
        self.breadth = breadth
    }
    
    override func calculateArea() {
        super.calculateArea()
        area = length * breadth
    }
}

let square: Square = Square(side: 10.0)
square.calculateArea()
square.printArea()

let rectangle: Rectangle = Rectangle(length: 10.0, breadth: 5.0)
rectangle.calculateArea()
rectangle.printArea()
```

## ๐ธ๋ฐ์ดํฐ ์บก์ํ

```objectivec
#import <Foundation/Foundation.h>

@interface Adder : NSObject
//@property(nonatomic, readonly) NSInteger total;

- (id)initWithInitialNumber:(NSInteger)initialNumber;
- (void)addNumber:(NSInteger)newNumber;
- (NSInteger)getTotal;

@end

@implementation Adder {
    NSInteger total;
}

//@synthesize total;

- (id)initWithInitialNumber:(NSInteger)initialNumber {
    self = [super init];
    total = initialNumber;
    return self;
}

- (void)addNumber:(NSInteger)newNumber {
    total = total + newNumber;
}

- (NSInteger)getTotal {
    return total;
}

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        Adder *adder = [[Adder alloc] initWithInitialNumber:10];
        [adder addNumber:5];
        [adder addNumber:4];
        
//        NSLog(@"The total is %ld", adder.total);
        NSLog(@"The total is %ld", [adder getTotal]);
    }
    return 0;
}
```

## ๐ธ์นดํ๊ณ ๋ฆฌ

```objectivec
#import <Foundation/Foundation.h>

// ์นดํ๊ณ ๋ฆฌ ๋ง๋ค๊ธฐ ์์ 
@interface NSString(MyAddtions)
+(NSString *)getCopyRightString;    // ์ ์๊ถ์ ์ด๋ฆ ์๋ ค์ฃผ๋ ํด๋์ค ๋ฉ์๋
-(NSString *)getName;
@end

@implementation NSString(MyAddtions)

+(NSString *)getCopyRightString {
    return @"์ ์๊ถ์ ๋ฉ์์ด์ฌ์์ฒ๋ผ 2022";
}

-(NSString *)getName {
    return @"ned";
}

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        NSLog(@"%@", [NSString getCopyRightString]);
        
        NSString *temp = [[NSString alloc] init];
        NSLog(@"%@", [temp getName]);
    }
    return 0;
}
```
