
## πΈν¨μ

Functions

- ν¨μλ μμμ ν¨κ² μννλ λͺλ Ήλ¬Έμ κ·Έλ£Ήμλλ€.
- λͺ¨λ  objective-cνλ‘κ·Έλ¨μλ  main() μ΄λΌλ νλμ cν¨μκ° μμΌλ©° κ°μ₯ μ¬μν νλ‘κ·Έλ¨μ λͺ¨λ μΆκ° ν¨μλ₯Ό μ μν  μ μμ΅λλ€.
    - μ½λλ₯Ό λ³λμ κΈ°λ₯μΌλ‘ λλ μ μμ΅λλ€.
- μ½λλ₯Ό μ¬λ¬ κΈ°λ₯μΌλ‘ λλλ λ°©λ²μ μ¬μ©μμκ² λ¬λ € μμ§λ§ λΌλ¦¬μ μΌλ‘ κ΅¬λΆμ μΌλ°μ μΌλ‘ κ° κΈ°λ₯μ΄ νΉμ  μμμ μννλλ‘ ν©λλ€.
- ν¨μ **μ μΈ**μ μ»΄νμΌλ¬μκ² ν¨μμ μ΄λ¦, λ°ν μ ν λ° λ§€κ°λ³μμ λν΄ μλ €μ€λλ€.
    - ν¨μ **μ μ**λ ν¨μμ μ€μ  λ³Έλ¬Έμ μ κ³΅ν©λλ€.
    - κΈ°λ³Έμ μΌλ‘ objective0-cμμλ ν¨μλ₯Ό λ©μλλΌκ³  λΆλ¦λλ€.
- objective-c κΈ°λ° νλ μμν¬λ νλ‘κ·Έλ¨μμ νΈμΆν  μ μλ μλ§μ κΈ°λ³Έ μ κ³΅ λ©μλλ₯Ό μ κ³΅ν©λλ€.
    - Ex), λ€λ₯Έ λ¬Έμμ΄μ λ¬Έμμ΄μ μΆκ°νλ €λ©΄ **appendString() λ©μλ**λ₯Ό μ¬μ©ν©λλ€.
- λ©μλλ ν¨μ, μλΈλ£¨ν΄, νλ‘μμ  λ±κ³Ό κ°μ΄ λ€μν μ΄λ¦μΌλ‘ μλ €μ Έ μμ΅λλ€.

---

## πΈλ©μλ μ μ

![Untitled](https://user-images.githubusercontent.com/67450169/194752533-3b010132-9fe2-4b73-8bf1-63b4471b3885.png)## πΈλ©μλ μ μ

![Untitled (1)](https://user-images.githubusercontent.com/67450169/194752535-b87a2351-30f8-447c-b2d8-4819cb858d36.png)```objectivec
#import <Foundation/Foundation.h>

@interface MyNumber: NSObject
- (int)getMaxiumNumberWithFirstNumber:(int)num1 secondNumber:(int)num2;
@end

@implementation MyNumber
- (int)getMaxiumNumberWithFirstNumber:(int)num1 secondNumber:(int)num2 {
    
    int result;
    
    if (num1 > num2) {
        result = num1;
    } else {
        result = num2;
    }
    
    return result;
}
@end

int main (int argc, const char * argv[])
{
    MyNumber *num = [[MyNumber alloc] init];
    int maxNum = [num getMaxiumNumberWithFirstNumber:13 secondNumber:10];
    printf("%d", maxNum);
   return 0;
}
```

## πΈλ©μλ μ μΈ

![Untitled (2)](https://user-images.githubusercontent.com/67450169/194752541-0e3c35bd-c516-4eac-8d12-78de51f5a25d.png)---

![Untitled (3)](https://user-images.githubusercontent.com/67450169/194752542-a1189670-74a5-47d5-aba0-f2f1112053db.png)## πΈλ©μλ νΈμΆ

![Untitled (4)](https://user-images.githubusercontent.com/67450169/194752545-49153cbf-3218-4dd8-8d0f-e215c582c73c.png)---

## πΈν¨μμ μΈμ

- ν¨μκ° μΈμλ₯Ό μ¬μ©νλ €λ©΄ μΈμκ°μ νμ©νλ λ³μλ₯Ό μ μΈν΄μΌ νλλ€. μ΄λ¬ν λ³μλ₯Ό ν¨μμ **νμ λ§€κ°λ³μ**λΌκ³  ν©λλ€.
- νμμ λ§€κ°λ³μλ ν¨μ λ΄λΆμ λ€λ₯Έ μ§μ­ λ³μμ²λΌ μλνλ©° ν¨μμ λ€μ΄κ° λ μμ±λκ³  μ’λ£ν  λ μλ©Έλ©λλ€.
- ν¨μλ₯Ό νΈμΆνλ λμ μΈμλ₯Ό ν¨μμ μ λ¬ν  μ μλ λ κ°μ§ λ°©λ²μ΄ μμ΅λλ€.

![Untitled (5)](https://user-images.githubusercontent.com/67450169/194752550-b6ed3ec5-85f9-4425-b2bd-a7010e12eb97.png)
```objectivec
#import <Foundation/Foundation.h>

@interface MyNumber: NSObject
- (int)getMaxiumNumberWithFirstNumber:(int)num1 secondNumber:(int)num2;
- (NSString *)getHello;
@end

@implementation MyNumber
- (int)getMaxiumNumberWithFirstNumber:(int)num1 secondNumber:(int)num2 {
    
    int result = num1 > num2 ? num1: num2;
    
    return result; // call by value
}

- (NSString *)getHello {
    NSString *hello = @"Hello World";
    return hello; // call by reference
}
@end

int main (int argc, const char * argv[])
{
    MyNumber *num = [[MyNumber alloc] init];
    int maxNum = [num getMaxiumNumberWithFirstNumber:13 secondNumber:20];
    NSLog(@"%d", maxNum);
    
    NSString *hello = [num getHello];
    NSLog(@"%@", hello);
   return 0;
}
```

---

## πΈλΈλ‘(ν΄λ‘μ μ μ‘°μλ)

- objective-c ν΄λμ€λ κ΄λ ¨ λμκ³Ό λ°μ΄ν°λ₯Ό κ²°ν©νλ κ°μ²΄λ₯Ό μ μν©λλ€.
- λλ‘λ λ©μλ λͺ¨μμ΄ μλλΌ λ¨μΌ μμμ΄λ λμ λ¨μλ₯Ό λνλ΄λ κ²μ΄ ν©λ¦¬μ μλλ€.

- λΈλ‘μ c,objective-c λ° c++μ μΆκ°λ μΈμ΄ μμ€ κΈ°λ₯μΌλ‘, μ΄λ₯Ό ν΅ν΄ λ§μΉ κ°μΈ κ²μ²λΌ λ©μλλ ν¨μμ μ λ¬ν  μ μ κ³ μ ν μ½λ μΈκ·Έλ¨ΌνΈλ₯Ό λ§λ€ μ μμ΅λλ€.
- λΈλ‘μ NSArray λλ NSDictionaryμ κ°μ μ»¬λ μμ μΆκ°ν  μ μμμ μλ―Ένλ objective-c κ°μ²΄μλλ€
- λν μν΄λ‘μ§ λ²μμμ κ°μ μΊ‘μ²νμ¬ λ€λ₯Έ νλ‘κ·Έλλ° μΈμ΄μ **ν΄λ‘μ ** λλ **λλ€**μ μ μ¬νκ² λ§λλ κΈ°λ₯μ΄ μμ΅λλ€.

---

## πΈλ¨μ λΈλ‘ μ μΈ κ΅¬λ¬Έ

![Untitled (6)](https://user-images.githubusercontent.com/67450169/194752414-fdfd172b-479f-4709-a96d-4d5bf01fede7.png)
- κ°λ¨ν λΈλ‘ κ΅¬ν

![Untitled (7)](https://user-images.githubusercontent.com/67450169/194752415-6b0eea39-a21e-400c-a721-7ae23c6d8280.png)
![Untitled (8)](https://user-images.githubusercontent.com/67450169/194752419-8e6cee0e-c968-466e-9590-15593c6fb1db.png)
---

![Untitled (9)](https://user-images.githubusercontent.com/67450169/194752574-f201edc2-04be-44a4-aee4-b3c65aab350a.png)---

## πΈ μ ν μ μλ₯Ό μ¬μ©νλ λΈλ‘

![Untitled (10)](https://user-images.githubusercontent.com/67450169/194752427-e01c09e5-ec93-41a4-9397-2df4b4f4a103.png)
---

```objectivec
#import <Foundation/Foundation.h>

// CμΈμ΄ μ€νμΌμ ν¨μ
double multiplyTwoValuesOrgin(double firstValue, double secondValue)
{
    return firstValue * secondValue;
}

// BlockμΌλ‘ λ€μ μ ν¨μλ₯Ό μ¨λ³Έλ€λ©΄
// Blockμ μ΄λ¦μ (^multiplyTwoValues)(double, double)
// Blockμ μ€μ  μλλ΄μ©μ ^{ ... }μΌλ‘ κ΅¬ν
double (^multiplyTwoValues)(double, double) = ^(double firstValue, double secondValue){
    return firstValue * secondValue;
};

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        // insert code here...
        NSLog(@"Hello, World!");
        
        double myNum = multiplyTwoValues(2, 4);
        NSLog(@"%f", myNum);
    }
    return 0;
}
```

---

```objectivec
#import <Foundation/Foundation.h>

typedef void (^CompletionBlock)();

@interface SampleClass: NSObject
- (void)performActionWithCompletion:(CompletionBlock)completionBlock;
@end

@implementation SampleClass

- (void)performActionWithCompletion:(CompletionBlock)completionBlock {
    NSLog(@"Action performed");
    completionBlock();
}

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        NSLog(@"Hello, World!");
        
        SampleClass *sampleClass = [[SampleClass alloc] init];
        [sampleClass performActionWithCompletion:^{
            NSLog(@"Completion is called to intimate action is performed.");
        }];
    }
    return 0;
}
```

---

## πΈ μ«μ

![Untitled (11)](https://user-images.githubusercontent.com/67450169/194752435-e065f56f-6ed4-4329-9209-2eb01d4346bb.png)
![Untitled (12)](https://user-images.githubusercontent.com/67450169/194752438-884ba50f-b59b-4f13-94c6-951079c7b31f.png)
![Untitled (13)](https://user-images.githubusercontent.com/67450169/194752443-740a9f3e-6180-4e43-a44c-9bb2777f777c.png)
---

```objectivec
#import <Foundation/Foundation.h>

// Foundationμ΄ μ κ³΅νλ NSObjectλ₯Ό μμλ°μ SampleClassλ μ΄λ¬ν λ΄μ©μ κ΅¬νν©λλ€.
@interface SampleClass : NSObject
- (NSNumber *)multiplyA:(NSNumber *)a withB:(NSNumber *)b;
@end

// SampleClassμ κ΅¬μ²΄μ μΈ λ΄μ©μ λ€μκ³Ό κ°μ΅λλ€.
@implementation SampleClass

- (NSNumber *)multiplyA:(NSNumber *)a withB:(NSNumber *)b {
    
    // NSNumber νμμΌλ‘ λ°μ aμ bλ‘λΆν° float κ°λ€μ κΊΌλ΄μ κ³±μν ν
    float number1 = [a floatValue];
    float number2 = [b floatValue];
    float product = number1 * number2;
    
    // κ²°κ³Όλ₯Ό NSNumberλ‘ λ€μ λ§λ€μ΄ λ°ννλ€.
    NSNumber *result = [NSNumber numberWithFloat:product];
    return result;
}

@end

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        NSLog(@"Hello, World!");
        
        // swiftμλ€λ©΄ ... var sampleClass: SampleClass = SampleClass()
        SampleClass *sampleClass = [[SampleClass alloc] init];
        
        NSNumber *a = [NSNumber numberWithFloat:10.5];
        NSNumber *b = [NSNumber numberWithFloat:10.0];
        NSNumber *result = [sampleClass multiplyA:a withB:b];
        
        // κ²°κ³Όμ NSNumberλ‘λΆν° NSStringλ₯Ό λ§λ€μ΄ νμ©νλ€.
        NSString *resultString = [result stringValue];
        NSLog(@"The product is %@", resultString);
    }
    return 0;
}
```

---

## πΈ λ°°μ΄

![Untitled (14)](https://user-images.githubusercontent.com/67450169/194752448-ffd93136-6e50-4aae-8d82-fb7fc53e9644.png)
## πΈ λ°°μ΄μ μΈ

![Untitled (15)](https://user-images.githubusercontent.com/67450169/194752455-c6e9984d-cb13-4e8c-9bf1-1d166705f075.png)
---

```objectivec
#import <Foundation/Foundation.h>

int main(int argc, const char * argv[]) {
    @autoreleasepool {
        
        int myArray[10];    // 10κ°μ intκ°μ΄ λ€μ΄κ° λ°°μ΄ μ μΈ
        int i, j;           // for λ°λ³΅λ¬Έμ νμ©
        
        for (i = 0; i < 10; i++) { // iλ 0..<10 κ΅¬κ°μΌλ‘ μ¦κ°νλ©° λ°λ³΅
            myArray[i] = i + 100;
        }
        
        for (j = 0; j < 10; j++) {
            NSLog(@"Element[%d] = %d\n", j, myArray[j]);
        }
        
    }
    return 0;
}
```

---

![Untitled (16)](https://user-images.githubusercontent.com/67450169/194752457-8f0d83e8-6d37-4761-9133-89789be541db.png)
---

## πΈ ν¬μΈν° pointer

```objectivec
#import <Foundation/Foundation.h>

int main(int argc, const char * argv[]) {

    int age = 13;
    double height = 145.32;
    
    // λ³μμ λ΄κΈ΄ κ°μ μΆλ ₯
    NSLog(@"value of age : %d", age);
    NSLog(@"value of hegith : %f", height);
    
    // λ³μκ° μμΉν λ©λͺ¨λ¦¬ μμμμ μ£Όμ
    NSLog(@"address of age : %x", &age);
    NSLog(@"address of height : %x", &height);
    
    // ν¬μΈν° μ λ³΄ = ν΄λΉ λ°μ΄ν°μ λ©λͺ¨λ¦¬ μ£Όμ + λ©λͺ¨λ¦¬λ₯Ό μ°¨μ§νλ ν¬κΈ°
    // ν μ§λμ₯ = μ£Όμμ§(κ²½μλΆλ μΈλ¦κ΅°...) + λͺ νμ μ λ³΄(μμΌ 13ν)
    
    return 0;
}
```

```objectivec
#import <Foundation/Foundation.h>

int main(int argc, const char * argv[]) {
    // ν¬μΈν° μ λ³΄ = ν΄λΉ λ°μ΄ν°μ λ©λͺ¨λ¦¬ μ£Όμ + λ©λͺ¨λ¦¬λ₯Ό μ°¨μ§νλ ν¬κΈ°
    // ν μ§λμ₯ = μ£Όμμ§(κ²½μλΆλ μΈλ¦κ΅°...) + λͺ νμ μ λ³΄(μμΌ 13ν)

    int index = 17;
    printf("i stores its value at %x\n", &index);
    printf("this function starts at %x\n", &main);
    
    return 0;
}
```

```objectivec
#import <Foundation/Foundation.h>

int main(int argc, const char * argv[]) {
    // ν¬μΈν° μ λ³΄ = ν΄λΉ λ°μ΄ν°μ λ©λͺ¨λ¦¬ μ£Όμ + λ©λͺ¨λ¦¬λ₯Ό μ°¨μ§νλ ν¬κΈ°
    // ν μ§λμ₯ = μ£Όμμ§(κ²½μλΆλ μΈλ¦κ΅°...) + λͺ νμ μ λ³΄(μμΌ 13ν)

    int age = 17;
    
    // λ³μ ageμ μ£Όμλ₯Ό νμΈν΄μ, int νμμ΄ λ΄κΈΈ κ±°λΌκ³  μκ°νλ ν¬μΈν° λ³μ λ§λ€κΈ°
    int *addressOfAge = &age;
    
    NSLog(@"ageλ %p μ£Όμμ μμΉνμ΅λλ€.", addressOfAge);
    NSLog(@"%p μ£Όμμ κ°λ³΄λ %d κ°μ΄ λ€μ΄μμ΅λλ€.", addressOfAge, *addressOfAge);
    
    /*
     μΆλ ₯λ¬Έ:
     ageλ 0x16fdff3ac μ£Όμμ μμΉνμ΅λλ€.
     0x16fdff3ac μ£Όμμ κ°λ³΄λ 17 κ°μ΄ λ€μ΄μμ΅λλ€.
     */
    
    return 0;
}
```

```objectivec
#import <Foundation/Foundation.h>

@interface SampleClass : NSObject
- (void)sayHello;
@end

@implementation SampleClass
- (void)sayHello {
    NSLog(@"Hello World");
}
@end

int main(int argc, const char * argv[]) {
    // ν¬μΈν° μ λ³΄ = ν΄λΉ λ°μ΄ν°μ λ©λͺ¨λ¦¬ μ£Όμ + λ©λͺ¨λ¦¬λ₯Ό μ°¨μ§νλ ν¬κΈ°
    // ν μ§λμ₯ = μ£Όμμ§(κ²½μλΆλ μΈλ¦κ΅°...) + λͺ νμ μ λ³΄(μμΌ 13ν)

    int age = 17;
    
    // λ³μ ageμ μ£Όμλ₯Ό νμΈν΄μ, int νμμ΄ λ΄κΈΈ κ±°λΌκ³  μκ°νλ ν¬μΈν° λ³μ λ§λ€κΈ°
    int *infoOfAge = &age;
    
    NSLog(@"ageλ %p μ£Όμμ μμΉνμ΅λλ€.", infoOfAge);
    // ageλ 0x16fdff3ac μ£Όμμ μμΉνμ΅λλ€.
    
    NSLog(@"int νμμ λ©λͺ¨λ¦¬ ν¬κΈ°λ %zu λ°μ΄νΈμλλ€.", sizeof(int));
    // int νμμ λ©λͺ¨λ¦¬ ν¬κΈ°λ 4 λ°μ΄νΈμλλ€.
    NSLog(@"λ³μ ageμ λ©λͺ¨λ¦¬ ν¬κΈ°λ %zu λ°μ΄νΈμλλ€.", sizeof(age));
    // λ³μ ageμ λ©λͺ¨λ¦¬ ν¬κΈ°λ 4 λ°μ΄νΈμλλ€.
    NSLog(@"μ²μ %p μ£Όμμ κ°λ³΄λ %d κ°μ΄ λ€μ΄μμ΅λλ€.", infoOfAge, *infoOfAge);
    // μ²μ 0x16fdff3ac μ£Όμμ κ°λ³΄λ 17 κ°μ΄ λ€μ΄μμ΅λλ€.
    
    *infoOfAge = 32;
    NSLog(@"λ€μ %p μ£Όμμ κ°λ³΄λ %d κ°μ΄ λ€μ΄μμ΅λλ€.", infoOfAge, *infoOfAge);
    // λ€μ 0x16fdff3ac μ£Όμμ κ°λ³΄λ 32 κ°μ΄ λ€μ΄μμ΅λλ€.
    
    NSLog(@"intλ₯Ό λ΄μ λ°μ΄ν°μ ν¬μΈν°μ λ³΄ ν¬κΈ°λ %zu λ°μ΄νΈμλλ€.", sizeof(int *));
    // intλ₯Ό λ΄μ λ°μ΄ν°μ ν¬μΈν°μ λ³΄ ν¬κΈ°λ 8 λ°μ΄νΈμλλ€.
    NSLog(@"%pλ₯Ό κ°λ₯΄ν€λ μ λ³΄μ λ©λͺ¨λ¦¬ ν¬κΈ°λ %zu λ°μ΄νΈμλλ€.", infoOfAge, sizeof(infoOfAge));
    // 0x16fdff3acλ₯Ό κ°λ₯΄ν€λ μ λ³΄μ λ©λͺ¨λ¦¬ ν¬κΈ°λ 8 λ°μ΄νΈμλλ€.
    
    
    // SampleClassμ μΈμ€ν΄μ€λ₯Ό λ§λ€μ΄μ
    // κ·Έ λ©λͺ¨λ¦¬μ μμΉ μ λ³΄λ₯Ό SampleClassν΄λμ€μ λ§μΆ ν¬μΈν° λ³μ sampleClassμ ν λΉνλ€
    // ν΄λμ€μ μν΄ λ§λ€μ΄μ§λ μΈμ€ν΄μ€λ λ¬΄μ‘°κ±΄ ν¬μΈν° λ¨μλ‘ κ΄λ¦¬ν΄μΌλ§ νμ© κ°λ₯νλ€.
    SampleClass *sampleClass = [[SampleClass alloc] init];
    
    // sampleClass ν¬μΈν° μ λ³΄κ° κ°λ₯΄ν€λ μΈμ€ν΄μ€ λ°μ΄ν°λ₯Ό μ°Ύμκ°μ
    // λ°μ΄ν°μ λͺμλ sayHello λ©μλλ₯Ό μ€ννλΌ
    [sampleClass sayHello];
    
    
    return 0;
}
```

---

## πΈ λ¬Έμμ΄

- objective-c νλ‘κ·Έλλ° μΈμ΄μ λ¬Έμμ΄ NSStringμ μ¬μ©νμ¬ ννλλ©° νμ ν΄λμ€ NSMutableStringμ λ¬Έμμ΄ κ°μ²΄λ₯Ό μμ±νλ μ¬λ¬ λ°©λ²μ μ κ³΅ν©λλ€.
- λ¬Έμμ΄ κ°μ²΄λ₯Ό λ§λλ κ°μ₯ κ°λ¨ν λ°©λ²μ objective-c @ββ¦β κ΅¬λ¬Έμ μ¬μ©νλ κ²μλλ€.

![Untitled (17)](https://user-images.githubusercontent.com/67450169/194752460-1f1d9a42-506e-48d3-8258-0a6dd246a91c.png)
![Untitled (18)](https://user-images.githubusercontent.com/67450169/194752463-e551e195-dc5c-4172-9b29-058a83c89631.png)
---

![Untitled (19)](https://user-images.githubusercontent.com/67450169/194752467-883f62bd-be84-4f93-8a9b-6b4fbe3032ca.png)
---

![Untitled (20)](https://user-images.githubusercontent.com/67450169/194752472-d3c32cd9-ecf6-4f9a-b5fa-d684c43b479d.png)
---

![Untitled (21)](https://user-images.githubusercontent.com/67450169/194752473-1d065468-d8a3-4aed-bbe0-4f80dd81ea7b.png)
---

![Untitled (22)](https://user-images.githubusercontent.com/67450169/194752477-926fab98-1aa5-4566-8128-6f276ac32f9c.png)
---
