---
layout: post
title: Binary Lesson
toc: False
comments: True
---

```
def binary_to_decimal(b: str) -> int:
    """Convert a binary string to decimal integer."""
    try:
        return int(b, 2)
    except ValueError:
        raise ValueError(f"Invalid binary number: {b}")

def decimal_to_binary(n: int) -> str:
    """Convert a nonnegative integer to binary string."""
    if n < 0:
        raise ValueError("Negative numbers not supported for binary conversion.")
    return bin(n)[2:]

def operate(bin1: str, bin2: str, op: str) -> str:
    """Perform arithmetic on two binary numbers and return binary result."""
    x = binary_to_decimal(bin1)
    y = binary_to_decimal(bin2)
    if op == '+':
        result = x + y
    elif op == '-':
        result = x - y
    elif op == '*':
        result = x * y
    elif op == '/':
        if y == 0:
            raise ZeroDivisionError("Cannot divide by zero.")
        result = x // y
    else:
        raise ValueError(f"Unsupported operator: {op}")
    # For subtraction or division, result could be negative or zero.
    if result < 0:
        # represent negative results with a leading minus sign
        return '-' + decimal_to_binary(-result)
    return decimal_to_binary(result)

def main():
    print("=== Binary Calculator ===")
    print("Operations: +, -, *, /")
    print("Type 'conv' to convert decimal→binary, or 'exit' to quit.")
    while True:
        cmd = input("\nEnter command or first binary number: ").strip().lower()
        if cmd == 'exit':
            print("Goodbye!")
            break
        if cmd == 'conv':
            dec = input("Enter decimal integer: ").strip()
            try:
                n = int(dec)
                print(f"Binary: {decimal_to_binary(n)}")
            except ValueError:
                print("❌ Please enter a valid integer.")
            continue

        # Otherwise, treat cmd as first binary operand
        bin1 = cmd
        bin2 = input("Enter second binary number: ").strip()
        op   = input("Enter operator (+, -, *, /): ").strip()
        try:
            result = operate(bin1, bin2, op)
            print(f"\nResult: {bin1} {op} {bin2} = {result}")
        except Exception as e:
            print(f"❌ Error: {e}")

if __name__ == "__main__":
    main()
```