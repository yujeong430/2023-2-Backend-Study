# GDSC 백엔드 스터디 Week 1
### JAVA
1. 운영체제에 독립적
2. **객체지향**언어
3. 자동 메모리 관리
4. 네트워크와 분산처리를 지원
5. 멀티쓰레드를 지원
6. 동적 로딩을 지원
<br>
---
### 객체지향 프로그래밍
> 실세계처럼 프로그래밍에서 필요한 데이터를 추상화시켜 **상태와 행위를 가진 객체**로 만들고, 객체들간의 상호작용을 통해 로직을 구성하는 프로그래밍 방법.
<br>
#### 장점
1. 코드의 재사용성이 높다. (클래스 재사용, 상속을 통해 확장)
2. 유지보수가 쉽다. (수정해야 할 부분이 클래스 내부 멤버 변수 혹은 메소드로 존재재)
3. 대형 프로젝트에 적합하다. (클래스 단위로 모듈화)
#### 단점
1. 처리 속도가 상대적으로 느리다.
2. 객체가 많으면 용량이 커질 수 있다.
3. 설계 시 많은 노력과 시간이 필요하다.
<br>
#### 객체지향 프로그래밍 특징
1. **추상화**   
객체에서 공통된 속성과 행위를 추출하여 타입을 정의하는 과정. 불필요한 정보는 숨기고, 중요한 정보만을 표현하여 프로그램을 간단하게 만드는 것.
2. **캡슐화**   
변수와 함수를 하나로 묶는 것. 낮은 결합도를 유지할 수 있도록 설계. 속성과 기능을 정의하는 변수와 메소드를 클래스라는 캡슐에 넣어서 분류, 재사용이 원활하고 정보은닉을 활용할 수도 있음.
3. **상속**  
클래스의 속성과 행위를 하위클래스에 물려주는 것. 새로운 클래스가 기존 클래스의 데이터와 연산을 이용할 수 있음.
4. **다형성**   
하나의 변수명, 함수명이 상황에 따라 다른 의미로 해석될 수 있는 것. 하나의 클래스 내부에 같은 이름의 행위를 여러개 정의하거나, 상위 클래스의 행위를 하위 클래스에서 재정의하여 사용 가능.
<br>
#### 객체지향 설계 원칙(SOLID)
1. **단일 책임 원칙**   
하나의 클래스는 단 하나의 책임만 가져야 함.
2. **개방 - 폐쇄 원칙**   
소프트웨어 요소는 확장에는 열려있으나 변경에는 닫혀있어야 함.
3. **리스코프 치환 원칙**   
프로그램 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 함. (상위 타입을 사용하는 프로그램은 정상 동작)
4. **인터페이스 분리 원칙**   
범용 인터페이스 하나보다 클라이언트를 위한 여러 개의 인터페이스로 구성하는 것이 좋음.
5. **의존관계 역전 원칙**   
추상화에 의존해야지 구체화에 의존하면 안된다.

---
### 구현 과제
Main.java
``` java
public class Main {
    public static void main(String[] args) {
        Calculator calculator = new Calc();

        System.out.println("1234 + 4321 = " + calculator.plus(1234, 4321));
        System.out.println("911 - 170 = " + calculator.minus(911, 170));
        System.out.println("2 * 3 = " + calculator.mul(2, 3));
        System.out.println("33 / 11 = " + calculator.div(33, 11));

        System.out.println("\n");

        Cat cat = new Cat();
        Dog dog = new Dog();
        Animal[] animals = {cat, dog};
        for (Animal animal : animals) {
            animal.speak();
        }
    }
}
```
Calculator.java
```java
public interface Calculator {
    int plus(int a, int b); // a + b 값 반환
    int minus(int a, int b); // a - b 값 반환
    int mul(int a, int b); // a * b 값 반환
    int div(int a, int b); // a / b 값 반환
}
```
Calc.java
```java
public class Calc implements Calculator{
    public int plus(int a, int b){
        return a+b;
    }
    public int minus(int a, int b){
        return a-b;
    }

    public int mul(int a, int b){
        return a*b;
    }

    public int div(int a, int b){
        return a/b;
    }
}

```
Animal.java
```java
public abstract class Animal {
    public abstract void speak();
}

class Dog extends Animal{
    public void speak(){
        System.out.println("Dog says Woof!");
    }
}

class Cat extends Animal{
    public void speak(){
        System.out.println("Cat says Meow!");
    }
}
```