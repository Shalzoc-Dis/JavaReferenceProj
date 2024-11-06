Following this introduction: https://docs.google.com/presentation/d/1X0h0IZ9jCL88LLkT6qV2lcXYftOXGyi-lfK-U_IMPEY/mobilepresent?slide=id.g27bc11d9309_1_20

=Data Types=
| Data Type | Size   | Description                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------|
| byte      | 1 byte | Stores whole numbers from -128 to 127. Typically used to save memory in large arrays.       |
| short     | 2 bytes| Stores whole numbers from -32,768 to 32,767. Similar to byte but allows a wider range.      |
| int       | 4 bytes| Default data type for integers, storing values from -2^31 to 2^31-1.                        |
| long      | 8 bytes| Stores whole numbers from -2^63 to 2^63-1. Used when a wider range than int is needed.      |
| float     | 4 bytes| Stores fractional numbers with up to 6-7 decimal digits. Use "f" after the value (e.g., 1.2f). |
| double    | 8 bytes| Default for decimal values, stores fractional numbers with up to 15 decimal digits.         |
| boolean   | 1 bit  | Holds only two possible values: true and false. Used for conditional statements.           |
| char      | 2 bytes| Stores a single 16-bit Unicode character, from '\u0000' to '\uffff'.                       |

It is important to notice that decimal numbers are assumed to be doubles. To specify a float, an 'f' needs to 
be appended to it. e.g. 1.2f
This also applies to integers. They are assumed to be an int. However, adding an 'l' to the end specifies a long.
Long numbers can be broken up to increase readability using underscores, not commas. e.g. 1_234_567_890

==Casting==
Going from a smaller datatype to a bigger datatype is automatic. One needs to be explicit if going from a bigger to a smaller.

==Constants== 
Constants cannot be changed once they are defined in the program. Constants are marked with the "final" keyword.
```Java
final int maxAngle = 180;
```
==Enums==
```Java
enum Level {
  LOW,
  MEDIUM, 
  HIGH
}
```

==Bitwise Operators==
| Operator | Name                | Description                                                                                                  |
|----------|----------------------|--------------------------------------------------------------------------------------------------------------|
| &        | AND                 | Performs a bitwise AND operation. Each bit in the result is 1 only if the corresponding bits in both operands are 1. |
| \|       | OR                  | Performs a bitwise OR operation. Each bit in the result is 1 if at least one of the corresponding bits in either operand is 1. |
| ^        | XOR                 | Performs a bitwise XOR operation. Each bit in the result is 1 if the corresponding bits in the operands are different. |
| ~        | NOT (Complement)    | Inverts all bits, turning 1s to 0s and 0s to 1s. It’s a unary operator, only needing one operand.              |
| >>       | Right Shift         | Shifts bits to the right, discarding the rightmost bits. The leftmost bits are filled based on the sign of the original value. |
| <<       | Left Shift          | Shifts bits to the left, filling the rightmost bits with 0s. Each shift to the left doubles the value.       |
| >>>      | Unsigned Right Shift| Shifts bits to the right, filling the leftmost bits with 0 (ignores the sign). Works the same as `>>` for positive values. |
| <<<      | No Operation        | **Not a valid operator in Java.** Java does not have a "<<<" operator.                                          |

===AND===
This compares each bit of a number with the AND operation. This is often used for masking, where one wants to extract specific bits.
```Java
int a = 5;        // Binary: 0101
int b = 3;        // Binary: 0011
int result = a & b; // Result: 0001 (decimal 1)
```

===OR===
Like AND, this compares two numbers' binary representation using OR. This is often used when wanting to change specific bits.
```Java
int a = 5;        // Binary: 0101
int b = 3;        // Binary: 0011
int result = a | b; // Result: 0111 (decimal 7)
```

===XOR===
This is often used to toggle bits.
```Java
int a = 5;        // Binary: 0101
int b = 3;        // Binary: 0011
int result = a ^ b; // Result: 0110 (decimal 6)
```

===NOT===
This is a unary operator that inverts each bit of the operand. This effectively negates the number and subtracts 1.
~a == (-a - 1)
```Java
int a = 5;        // Binary (32-bit): 0000 0000 0000 0000 0000 0000 0000 0101
int result = ~a;    // Result: 1111 1111 1111 1111 1111 1111 1111 1010 (decimal -6)
```

===Left Shift===
This shifts the bits of a number left by a specified number of bits. 0s are filled to the right. Shifting by 1 effectively 
multiplies by 2, shifting by 2, multiplies by 4, etc.
```Java
int x = 5;         // In binary: 0000 0101
int result = x << 1; // Shift left by 1 bit: 0000 1010
// result is now 10 (5 * 2)
```

===Right Shift===
This is just like left shift, except that is shifts right. This is how one can divide and disregard the remainder. For signed 
numbers, the sign bit (the right most bit) is preserved.
```Java
int y = 20;        // In binary: 0001 0100
int result = y >> 1; // Shift right by 1 bit: 0000 1010
// result is now 10 (20 / 2)
```

===Unsigned Right Shift===
This is just like normal right shift, except that always fills in 0s.
```Java
int z = -20;       // In binary (32-bit signed): 1111 1111 1111 1111 1111 1111 1110 1100
int result = z >>> 1; // Unsigned right shift by 1 bit: 0111 1111 1111 1111 1111 1111 1111 0110
// result is now a large positive integer (2147483638), treating the number as unsigned
```

```Java 
.toBinaryString()
```
does what it says on the box.

==Assignment and Bitwise Operators==
Math and bitwise operators can be combined. This is like += and *=. 
```Java
int x += 3; // This is equivalent to int x = x + 3;
int x &= 3; // This is equivalent to int x = x & 3;
```

=Functions=
```Java
static int add(int a, int b) {
  return a + b;
}
static doNothing(String optional) {
  boolean 1 = false;
}
```
A constructor is a function with the same name as the class. Constructors can call other constructors.
The `new` keyword is used when executing a constructor instead of assigning a value. To create an object:
```Java
Wheel myWheel = new Wheel();
```

==Static Functions==
These are functions that do not need to be called via an object. They do need to be called via a class.

==Interfaces==
Interfaces are definitions of the functions that a class must implement. (Like C++ virtual)
Defining an Interface:
```Java
interface Robot {
  public void drive(float distance, int power);
  public void turn(float degrees);
}
```
Using an Interface:
```Java
class MyRobot implements Robot {
  public void drive(float distance, int power) {
    // Do something...
  }
}
```

=Inheritance=
This is a way to create classes that use code from other classes. This involves parent and child classes.
- Parent classes have functions and variables that can be used by child classes.
```Java
class Amimal {
  String sound;
  Animal() {
    this.sound = "Roar";
  }
  void speak() {
    System.out.println(this.sound);
  }
}

class Dog extends Animal {
  Dog() {
    super();
    this.sound = "Bark";
  }
}

Animal dog = new Dog();
dog.speak();
```
It is important to note that the `super()` method in a constructor calls the constructor of the parent class.
Functions can be overridden. If they are not, the parent's function definition will be used.

==Method Reference==
This is denoted with a double colon. It points to a method/function. 
- Essentially creates are variable that can be used as a function. 
- Good for passing a function to another function.
//TODO Look into this again.
//TODO Look into lambdas.

