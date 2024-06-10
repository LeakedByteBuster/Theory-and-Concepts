# BitShitfting

## Index
- [Logical Operators](#logical-operators)
- [Check value of a bit](#checking-the-value-of-a-bit)
- [Setting bit n](#setting-the-bit-n)
- [Clearing bit n](#clearing-bit-n)
- [Flipping bit n](#flipping-bit-n)

**BitMasks is a sequence of bits (0s and 1s) that is used to manipulate or isolate specific bits within a larger set of bits.**

## logical operators
- **^** : XOR operator
- **~** : NOT operator
- **&** : AND operator
- **|** : OR operator

## Checking the value of a bit
**ANDing the value of 2^n with the bit storage**

*(x >> n) & 1 | OR | bit = x & (1 << n) | OR | bit = (x & (1 << n)) != 0*

- x : integer
- n : shift to right/left by n positon

``` c

int  x = 2 >> 1;
int  n = sizeof(int) * 8 -1;
int  bit = 0;

for (; n >= 0;n--){
  bit = x & (1 << n);
  printf("%d", (bit != 0) ? 1 : 0); // or,
  // printf("%d", (x >> n) & 1);
  if (n%8 == 0)
      printf(" ");
}
puts("\n");

```

## Setting The Bit n
**ORing the value of the x variable with the value 2^n.**

*x |= (1 << 0)*

``` c
int  x = 2; // 00000000 00000000 00000000 00000010

x |= (1 << 0); // 00000000 00000000 00000000 00000011
printf("x = %d\n", x); // now, x = 3
```

## Clearing bit n
**ANDing the value of the x variable with the inverse (NOT) of the value 2^n**

*x &= ~(1 << 1)*

``` c
/* (e.g.)
* ~(1 << 1)   : 11111111 11111111 11111111 11111101
* ~(1 << 0)   : 11111111 11111111 11111111 11111110
* ~(1 << 31)  : 01111111 11111111 11111111 11111111
* and so on...
*/

int  x = 2; // 00000000 00000000 00000000 00000010

x &= ~(1 << 1); // 00000000 00000000 00000000 00000000
printf("x = %d\n", x); // now, x = 0

//****************************************************//

x = 2147483647 // 01111111 11111111 11111111 11111111
n = sizeof(int) * 8 -1; // n = 31
for (int i = n; i > 7; i--){
	x &= ~(1 << i); // clearing nth bit at each iteration, but last 7 bits
}
// After, loop finishes :
// x = 255 || 00000000 00000000 00000000 11111111

```

## Flipping bit n
**XORing the value of the x variable with 2^n**

``` c
int  x = 2; // 00000000 00000000 00000000 00000010

x ^= (1 << 3); // 00000000 00000000 00000000 00001010
printf("x = %d\n", x); // now, x = 10
```
