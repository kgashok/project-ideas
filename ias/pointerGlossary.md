#Pointers 

|Item | Interchangeable with | Description | Example |
|:----------|:----------|:------------|:-------------------|
|Integer	| Whole number | Any whole number value from 1 to 100000| 9930
|Integer variable | - | a variable type that can be initialized with _only_ a decimal value, e.g. **2220**) | int a_variable = 2220; | 

|Item | Interchangeable with | Description | Example |
|:----------|:----------|:------------|:-------------------|
|Pointer	| Memory location address |A valid memory location value in hexadecimal | 0x80005|
|Pointer variable | Pointer | a variable type that can be initialized _only_ with a memory address (_a.k.a._ **Pointer**) of other variables and not an integer (say decimal **2220**) | int* **pA**; pA = &a; | 
|Pointer type | Data type | refers to the type of the data retrieved or stored when *de-referencing* (using the `*` operator) a pointer variable | **int*** p; **char*** c; **float*** f;  | 
|Integer pointer | Integer Pointer Variable | When *de-referencing* (using the `*` operator) is used with the variable, it stores integer in the memory location | **int*** pInteger; *pInteger = 300;   | 
|Memory location value | Memory Address | Any physical memory location which can be accessed by the CPU | Any hexadecimal number between a range, say 0x1000 -> 0x10000 |
|Memory variable | Data variable | A human-defined name that might refer to one or more memory locations depending upon the type | **int a;** // 4 bytes starting at 0x4000 |
|Dereferencing | - | Using the `*` operator, retrieve or store a value in the memory location pointed to by the pointer variable | `*pA = 400;` | 
|Pointer in the LHS | - | Store data in the memory location pointed to | `*ppA = 23 + 39023;` 
|Pointer in the RHS | - | Retrieve data from the memory location pointed to | `int v = *ppA + 23;`  
|Invalid pointer assignments | - | Assigning an integer value as the address of a pointer | ppA = 23; // illegal because `23` is not a valid memory location | 
|Valid pointer assignments | - | Assigning a pointer variable to another pointer variable | If pA and pB are pointer variables, `pA = pB;`  |

### Code Quiz

#### Quiz 1
```cpp
int b; 
int* pA;
int* pB = &b; 
pA = pB;
printf ("%d is the value pointed to by pA\n", *pA); 
```
The string displayed is 
```
1. "pB is the value pointed to by pA"
2. "0 is the value pointed to by pA"
3. "2323443 is the value pointed to by pA"
4. Non-determinable because integer `b` is not initialized 
```

#### Quiz 2
```cpp
char buf[] = "this is a long string"; 
char* pBuf = buf; 
char* pBuf2; 
pBuf2 = pBuf;   // valid pointer to pointer assignment 
char* anotherP = (char *)malloc (sizeof(buf) * sizeof(char) ); 
*anotherP = *pBuf; 
printf ("%s is the contents of anotherP\n", anotherP); 
printf ("%c is the contents of anotherP\n", *anotherP);

```
The 2-line output in the display is: 
```cpp
1. "this is a long string"  and "t"
2. "t" and "t"
3. Non-determinable and "t" 
```

#### Quiz 3
```cLang
#include <stdio.h> 
#include <stdlib.h> 

void swap (int*, int*); // declaring swap 
int* get_a_number();    // uses malloc() to dynamically allocate integers

void swap(int *q,int *p)  // definition of swap 
{
    // Step 0 your code goes below

}

int main ()
{
    //------------------------------------------------------//
    /* do not edit*/ int *a = get_a_number();   // do NOT EDIT
    /* do not edit*/ int *b = get_a_number();   // do NOT EDIT
    /* do not edit*/ int  c = *get_a_number();  // do NOT EDIT
    /* do not edit*/ int  d = *get_a_number();  // do NOT EDIT
    //------------------------------------------------------//

    // Step 0 implement swap function 
    
    // Step 1 call the swap functions appropriately with a and b

    // Step 2 call the swap function appropriately with c and d

    // Step 3 print the numbers --------
    /* DO NOT EDIT */  printf ("%d %d %d %d", *a,*b, c, d); 
    // -----------------------------
    
    return 0;
}

int* get_a_number()
{
    int* number = (int*) malloc ( sizeof (int) ); 
    scanf("%d", number);
    return number;
}

```

Assume you've entered the appropriate code for the `swap` function above. The correct code for `Step 1 and Step 2` is: 

	1. `swap (&a, &b)` and `swap (&c, &d); `  
	2. `swap (*a, *b)` and `swap (&c, &d); `  
	3. `swap (a, b)` and `swap (c, d); `  
	4. `swap (a, b)` and `swap (&c, &d); `  
	5. None of the above   