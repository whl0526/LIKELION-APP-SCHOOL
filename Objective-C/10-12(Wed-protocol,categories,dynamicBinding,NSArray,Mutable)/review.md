
## πΈνλ‘ν μ½

```objectivec
#import <Foundation/Foundation.h>

// Objective-Cμμλ μ΄λ° μΌμ ν΄μ€ ν΄λμ€λ₯Ό μ°Ύλλ€λ©΄μ DelegateλΌκ³  νννλ€.
// (Delegate: μμμ, λνμ)
@protocol PrintProtocolDelegate
@optional
- (void)processCompleted;
@end

@interface PrintClass : NSObject {
    // λ΄κ° μμμλ‘μ κ·Έ μΌμ νκ² λ€λ λ°κ° μμΌλ©΄ κ·Έκ² λ°λ‘ delegate
    // idλ "μ΄λ€ Objective-C κ°μ²΄λ₯Ό κ°λ¦¬ν€λ ν¬μΈν°"
    id delegate;
}

// μ΄ ν΄λμ€κ° μνλ μΌμ λμ  ν΄μ€ delegate κ°μ²΄λ₯Ό μ§μ νλ λ©μλ
- (void)setDelegate:(id)newDelegate;
- (void)printDetails;
@end

@implementation PrintClass

- (void)setDelegate:(id)newDelegate {
    delegate = newDelegate;
}

- (void)printDetails {
    NSLog(@"Print Details");
    
    // deleage κ°μ²΄κ° PrintProtocolDelegate νλ‘ν μ½μ μ λ°λ₯Έλ€λ©΄
    // processCompleted λ©μλκ° μκΈ° λλ¬Έμ νΈμΆ κ°λ₯νλ€
    // λ νμ€ν νκΈ°μν΄ ν΄λΉ λ©μλκ° μ€νκ°λ₯νμ§ μ²΄ν¬ν΄λ³΄λ μ΅κ΄μ΄ μ’λ€.
    if ([delegate respondsToSelector:@selector(processCompleted)]) {
        [delegate processCompleted];
//        [delegate performSelector:@selector(processCompleted)];
    }
}

@end

@interface SampleClass : NSObject<PrintProtocolDelegate>
- (void)startAction;
@end

@implementation SampleClass

- (void)startAction {
    PrintClass *printClass = [[PrintClass alloc] init];
    
    // PrintClass ν΄λμ€λ‘ λ§λ€μ΄μ§ printClass μΈμ€ν΄μ€ κ°μ²΄μκ²
    // λ΄κ° λμ delegateκ° λμ΄μ€κ» λΌκ³  λ§ν΄μ€λ€.
    // PrintProtocolDelegate νλ‘ν μ½μ λ°λΌμ£ΌλκΉ
    // PrintClass ν΄λμ€μμ μκ΅¬νλ delegate μ­ν μ μ ν΄μ€κ±°λΌ κΈ°λνλ€.
    [printClass setDelegate:self];
    
    [printClass printDetails];
}

- (void)processCompleted {
    NSLog(@"Printing Process Completed");
}
@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        SampleClass *sampleClass = [[SampleClass alloc] init];
        [sampleClass startAction];
    }
    return 0;
}
```

## πΈobj-cμμ μΉ΄νκ³ λ¦¬βοΈλ§ μλ©΄λλ€. (μ΅μ€νμ X)

---

## πΈκ°μ²΄, μΉ΄νκ³ λ¦¬, μ΅μ€νμ, κ·Έλ¦¬κ³  νλ‘ν μ½ **(λ€μλ³΄κΈ°)**

BMI κ³μ°

self

```objectivec
#import <Foundation/Foundation.h>

// BMI κ³μ°

@interface Person : NSObject {
    float heightInMeter;
    int weightInKilos;
}
@property(nonatomic, readwrite) float heightInMeter;
@property(nonatomic, readwrite) int weightInKilos;

- (float)bodyMassIndex;
@end

@implementation Person

@synthesize heightInMeter;
@synthesize weightInKilos;

- (float)bodyMassIndex {
    // selfλ λ©μλμ μ€ν μ£Όμ²΄κ° λλ κ°μ²΄μ ν¬μΈν°λ€.
    // κ°μ²΄κ° μμ μκ² λ©μμ§λ₯Ό λ³΄λ΄μΌν  λ μ΄ selfκ° μ¬μ©λλ€.
    float height = [self heightInMeter];
    return [self weightInKilos] / ( height * height);
}
@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        Person *person = [[Person alloc] init];
        person.heightInMeter = 1.5;
        person.weightInKilos = 50;
        NSLog(@"%f", [person bodyMassIndex]);
    }
    return 0;
}
```

## πΈμΉ΄νκ³ λ¦¬

 λ¬Έμμ΄ μμ λͺ¨μ λ¬Έμμ κ°―μλ₯Ό μμλ³΄λ €λ μΉ΄νκ³ λ¦¬

```objectivec
#import <Foundation/Foundation.h>

// λ¬Έμμ΄ μμ λͺ¨μ λ¬Έμμ κ°―μλ₯Ό μμλ³΄λ €λ μΉ΄νκ³ λ¦¬
@interface NSString(VowelCounting)
- (int)vowelCount;
@end

@implementation NSString(VowelCounting)

- (int)vowelCount {
    NSCharacterSet *charSet = [NSCharacterSet characterSetWithCharactersInString:@"aeiouyAEIOUY"];
    NSUInteger count = [self length];
    
    int sum = 0;
    int index = 0;
    
    for (index = 0; index < count; index++) {
        unichar charactor = [self characterAtIndex:index];
        if ([charSet characterIsMember: charactor]) {
            sum++;
        }
    }
    
    return sum;
}

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        NSString *string = @"I'm your father";
        NSLog(@"%@ has %d vowels", string, [string vowelCount]);
    }
    return 0;
}
```

## πΈλμ  λ°μΈλ©

- λμ  λ°μΈλ©μ μ»΄νμΌ μκ°μ΄ μλ λ°νμμ νΈμΆν  λ©μλλ₯Ό κ²°μ ν©λλ€.
- λμ  λ°μΈλ©μ νκΈ° λ°μΈλ© μ΄λΌκ³ λ ν©λλ€.
- Obj-cμμ λͺ¨λ  λ©μλλ λ°νμμ λμ μΌλ‘ ν΄κ²°λ©λλ€.
- μ€νλλ μ νν μ½λλ λ©μλ μ΄λ¦(μ νμ)κ³Ό μμ  κ°μ²΄μ μν΄ κ²°μ λ©λλ€.
- λμ λ°μΈλ©μ λ€νμ±μ κ°λ₯νκ² ν©λλ€.
- Ex), Rectangle λ° Squareλ₯Ό ν¬ν¨ν κ°μ²΄ μ»¬λ μμ κ³ λ €νμ­μμ€.
- κ° κ°μ²΄μλ κ³ μ ν printArea λ©μλ κ΅¬νμ΄ μμ΅λλ€.
- λ€μ μ½λμμ [anObject printArea] ννμμ μν΄ μ€νλμ΄μΌ νλ μ€μ  μ½λλ λ°νμμ κ²°μ λ©λλ€.
- λ°νμ μμ€νμ λ©μλ μ€νμ μν μ νκΈ°λ₯Ό μ¬μ©νμ¬ Objectμ ν΄λμ€κ° λ¬΄μμ΄λ  μ μ ν λ©μλλ₯Ό μλ³ν©λλ€.

---

```objectivec
#import <Foundation/Foundation.h>

// μ μ¬κ°ν μ λ³΄λ₯Ό λ΄μ ν΄λμ€
@interface Square : NSObject {
    float area; // λ©΄μ  μ λ³΄λ₯Ό λ΄μ λ΄λΆ λ³μ(ν΄λμ€ λ°μμλ μ κ·Ό λΆκ°)
}

- (void)calculateAreaOfSide:(CGFloat)side;  // λ€ λ³μ κΈΈμ΄κ° κ°μΌλ―λ‘ νλμ κΈΈμ΄λ§ κ°μ Έμλ λ©΄μ  κ³μ° κ°λ₯
- (void)printArea; // κ³μ°λ λ©΄μ μ μΆλ ₯νλ λ©μλ
@end

@implementation Square

- (void)calculateAreaOfSide:(CGFloat)side {
    area = side * side;
}

- (void)printArea {
    NSLog(@"The area of square is %f", area);
}
@end

// κ°λ‘ μΈλ‘ κΈΈμ΄κ° λ³κ°μΈ μΌλ°μ μΈ μ§μ¬κ°ν μ λ³΄μ ν΄λμ€
@interface Reactangle : NSObject {
    float area; // λ©΄μ  μ λ³΄λ₯Ό λ΄μ λ΄λΆ λ³μ(ν΄λμ€ λ°μμλ μ κ·Ό λΆκ°)
}

- (void)calculateAreaOfLength:(CGFloat)length andBreadth:(CGFloat)breadth;
- (void)printArea; // κ³μ°λ λ©΄μ μ μΆλ ₯νλ λ©μλ
@end

@implementation Reactangle

- (void)calculateAreaOfLength:(CGFloat)length andBreadth:(CGFloat)breadth {
    area = length * breadth;
}

- (void)printArea {
    NSLog(@"The area of reactangle is %f", area);
}
@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        Square *square = [[Square alloc] init];
        [square calculateAreaOfSide:10.0];
//        [square printArea];
        
        Reactangle *reactangle = [[Reactangle alloc] init];
        [reactangle calculateAreaOfLength:10.0 andBreadth:5.0];
//        [reactangle printArea];
        
        // [object printArea] λ©μλ μ€νμ
        // λ§€λ² objectμ printArea λ©μλκ° κ°κ° λ¬΄μμΈμ§ νμΈνκ³ 
        // ν΄λΉ λ§€μλλ‘ μ€νν΄μ, μλ‘ λ€λ₯Έ κ²°κ³Όκ° λμ¬ μ μλ€.
        id object = square;
        [object printArea]; // The area of square is 100.000000
        
        object = reactangle;
        [object printArea]; // The area of reactangle is 50.000000
        
        object = square;
        [object printArea]; // The area of reactangle is 50.000000
    }
    return 0;
}
```

- μμ exμμ λ³Όμ μλ―μ΄ printArea λ©μλλ λ°νμμ λμ μΌλ‘ μ νλ©λλ€.
- μ΄λ λμ  λ°μΈλ©μ μμ΄λ©° μ μ¬ν μ’λ₯μ κ°μ²΄λ₯Ό μ²λ§λΌ λ λ§μ μν©μμ λ§€μ° μ μ©ν©λλ€.

## πΈFoundation Framework

- μμ κΈ°λ³Έ μ νΈλ¦¬ν° ν΄λμ€ μΈνΈλ₯Ό μ κ³΅ν©λλ€.
- ν λΉ ν΄μ μ κ°μ μΌκ΄λλ κ·μΉμ λμνμ¬ μννΈμ¨μ΄ κ°λ°μ λ μ½κ² λ§λ­λλ€.
- μ λμ½λ λ¬Έμμ΄, κ°μ²΄ μ§μμ± λ° κ°μ²΄ λ°°ν¬λ₯Ό μ§μν©λλ€.
- μ΄μμ± ν₯μμ μν΄ OS λλ¦½μ± μμ€μ μ κ³΅ν©λλ€.
- νλ μμν¬λ Appleμ΄ μΈμν NeXTStep μμ κ°λ°νμΌλ©° μ΄λ¬ν κΈ°μ΄ ν΄λμ€λ Mac OS X λ° iOSμ μΌλΆκ° λμμ΅λλ€.
- NeXTStepμ μν΄ κ°λ°λμκΈ° λλ¬Έμ ν΄λμ€ μ μλ€ βNSβκ° μμ΅λλ€.

---

## πΈNSArray & NSMutableArray

```objectivec
#import <Foundation/Foundation.h>
int main() {
 NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];
 NSArray *array = [[NSArray alloc]
 initWithObjects:@"string1", @"string2",@"string3",nil];
 NSString *string1 = [array objectAtIndex:0];
 NSLog(@"The object in array at Index 0 is %@",string1);
 
 NSMutableArray *mutableArray = [[NSMutableArray alloc]init];
 [mutableArray addObject: @"string"];
 string1 = [mutableArray objectAtIndex:0];
 NSLog(@"The object in mutableArray at Index 0 is %@",string1); 
 
 [pool drain];
 return 0;
}
```
