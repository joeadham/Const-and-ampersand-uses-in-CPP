## Task 3 'Const' and '&' uses in C++

'Const' and '&' have many uses in C++. Therefore, I tried to gather all their uses in one website.




## Const


### Usage in data declaration:

#### **Syntax:**

```ruby
const declaration ;
member-function const ;

```

#### **Usage:**

const instructs the compiler that a variables value is constant and the programmer shouldn’t change it in the future.

**It can be used in the following scenarios:**

- Declaring a variable as a constant e.g.: 
```ruby
 const int pi = 3.14;
 ```
- Declaring the size of an array:
```ruby 
const int maxarray = 255;
char store_char[maxarray];
```
- Pointer declaration & altering the value of the element that pointer points at:
```ruby
   char *firstPointer = 0, *secondPointer;
   char *const constantPointer = firstPointer;
   *constantPointer = 'a';   // OK
   constantPointer = secondPointer;   // C3892 compilation error
```
- In the declaration of read-only functions e.g.: get functions.

*Note:* You cannot declare constructors or destructors with the const keyword.




### Usage in data declaration:

#### **Syntax:**

1. To declare the object pointed to by the pointer as const:
```ruby
const char *constantCharacterPointer;
const int *constantIntPointer;
```
2. To declare the address of the pointer as const:
```ruby
char * const constantPointerToCharElement;
```
*Note:* A const pointer of a given type can be assigned to a pointer of the same type. However, a pointer that is not const cannot be assigned to a const pointer e.g.:

```ruby
int *const constantPointer = 0;
int *normalPointer;

int main() {
normalPointer = constantPointer;
constantPointer = normalPointer;   // C3892 compile error
}
```



## '&' symbol

The & symbol is used in 2 cases in C++:
1.	As a bitwise (AND) operator
2.	As a pointer address of operator


### 1.Bitwise operator:

**Single &:**
A single '&' compares each bit of two variables and returns 1 for each bit if they are 1, otherwise it returns a 0 bit e.g.:
```ruby
#include <iostream>  
using namespace std;
 
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  

   cout << hex << ( a & b ) << endl;
}

```
*Output: 0*


**Double &&:**

Double && symbol is used to compare the values of two elements and returns true if they both are true, otherwise returns false e.g.:
```
#include <iostream>
using namespace std;

int main() {
   bool flag1 = true , flag2 = true , flag3 = false , flag4 = false;

    if (flag1 && flag2){
        cout<< "First test is successful"<<endl;
    }else{
        cout << "First test is unsuccessful"<<endl;
    }

    if (flag2 && flag3){
        cout<< "Second test is successful"<<endl;
    }else{
        cout << "Second test is unsuccessful"<<endl;
    }

    if (flag3 && flag4){
        cout<< "Third test is successful"<<endl;
    }else{
        cout << "Third test is unsuccessful"<<endl;
    }


}
```
*Output:*
```
First test is successful
Second test is unsuccessful
Third test is unsuccessful
```



### 2. Address of operator:

An '&' operator before a variable can be used to fetch its address from the memory


#### **Syntax:**

```ruby
int a = 10;
int *ptr = &a; //ptr now holds the address of a in the memory
```

#### **Usage:**

It can be used to find the address of a variable or using the address to change the value of the element it is holding e.g.:
```ruby
#include <iostream>
using namespace std;

int main () {
    int  a;
    int  *ptr;
    int  val;

    a = 3000;

    cout << "Value of a before alteration :" << a << endl;
    // store the address of a
    ptr = &a;
    *ptr = 2;
    cout << "Value of a after alteration :" << a << endl;


    // take the value available at ptr
    val = *ptr;
    
    cout << "Value of ptr :" << ptr << endl;
    cout << "Value of val :" << val << endl;

    return 0;
}

```
*Output:*
```ruby
Value of a before alteration :3000
Value of a after alteration :2
Value of ptr :0x61fe10
Value of val :2

```
