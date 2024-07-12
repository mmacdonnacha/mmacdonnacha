---
title: PicoCTF - 2warm
date: '2024-07-01 19:37:00'
description: 'Can you convert the number 42 (base 10) to binary (base 2)? '
categories: [picoCTF, picoCTF 2019]
tags: [picoctf, 'general-skills', picoctf-easy]
---

## Description

This challenge is part of the picoCTF2019 competition.  
It is a *General Skills* - Easy category.

The objective for this challenge is to convert the decimal value **42** to its
binary value.

There is multiple ways to solve it, programatically or by pen and paper.

## Pen and Paper

To solve this challenge using pen and paper, you divide **42** by 2 until you
reach 0 and keep track of the remainder.

```plaintext
42 / 2 = 21  Remainder: 0
21 / 2 = 10  Remainder: 1
10 / 2 =  5  Remainder: 0
 5 / 2 =  2  Remainder: 1
 2 / 2 =  1  Remainder: 0
 1 / 2 =  0  Remainder: 1
```

Once you have finished the division you count the remainder bottom to top.  
Decimal 42 = Binary 101010

## Python

To convert **42** into binary using python we use the `bin()` function.  
The `bin()` will convert an integer number to a binary string prefixed with "0b".

```python
dec = 42
binary = bin(dec)

print(binary[2:])
```

## Java

To do this in Java we use the `Integer.toBinaryString()` method.

```java
public class DecimalToBinary {
    public static void main(String[] args) {
        int decimalNumber = 42;
        String binary = Integer.toBinaryString(decimalNumber);
        
        System.out.println("Decimal Number: " + decimalNumber);
        System.out.println("Binary Equivalent: " + binary);
    }
}
```

## Flag

To complete the challenge you need to surround the binary value with
`picoCTF{********}` and submit the flag.
