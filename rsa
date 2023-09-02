#!/usr/bin/python3

import sys
import time
import math


def pollard_rho(n):
    if n % 2 == 0:
        return 2

    def f(x):
        return (x**2 + 1) % n

    x = 2
    y = 2
    d = 1

    while d == 1:
        x = f(x)
        y = f(f(y))
        d = math.gcd(abs(x - y), n)

    return d


def main():
    if len(sys.argv) != 2:
        print("Usage: factors <file>")
        return

    input_file = sys.argv[1]

    try:
        with open(input_file, 'r') as f:
            lines = f.readlines()

        start_time = time.time()

        for line in lines:
            num = int(line.strip())
            factor = pollard_rho(num)

            if factor == num:
                print(f"{num} is prime.")
            else:
                print(f"{num}={factor}*{num // factor}")

            if time.time() - start_time > 5:
                print("Time limit exceeded")
                return

    except FileNotFoundError:
        print(f"File not found: {input_file}")
        return


if __name__ == '__main__':
    main()
