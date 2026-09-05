  # CMPS 6610 Problem Set 01
## Answers

**Name:** Furkan Bilgin


Place all written answers from `assignment-01.md` here for easier grading.

1. **Asymptotic notation**

  - 1a

Yes. Because you can write $2^{n+1}$ as $2(2^n)$. $2$ is a constant we can just omit that. Meaning $2^{n+1} \in O(2^n)$.

Proof by limit:

1. $\lim \frac{2^{n+1}}{2^n} = \frac{2^{n+1}}{2^n} = 2$
2. Limit is a constant
3. $2^{n+1} \in O(2^n)$.

  - 1b

No. Because $2^{2^n}$ is double exponential growth, it grows much faster than $2^n$. Therefore $2^{2^n} \notin O(2^n)$

Proof by limit:

1. $\lim \frac{2^{2^n}}{2^n} = \lim 2^{2^n - n}$
2. $2^n - n \to \infty$
3. So the limit is $\infty$, meaning $2^{2^n} \notin O(2^n)$

  - 1c

No. $n^{1.01}$ is a polynomial function vs. $log^2n$ which is logaritmic. Any positive growing polynomial function outgrows any polylogarithmc grow $log^kn$. Therefore $n^{1.01} \notin O({log^2n})$

Proof by limit:

1. $\lim \frac{n^{1.01}}{\log^2 n}$.
2. Top is polynomial, bottom is polylog and polynomial outgrows  polylog, limit being $\infty$.
5. $n^{1.01} \notin O(\log^2 n)$.

  - 1d

Yes. $\Omega$ notation means asymptotic lower bound, and $f(x) \in \Omega(g(x))$ means $f(x)$ grows faster or equally as $g(x)$. Any positive polynomial power of n will always grow faster than any polylogarithmic function. Therefore $n^{1.01} \in \Omega({log^2n})$

Proof by limit:

1. Same limit as 1c
2. $\lim \frac{n^{1.01}}{\log^2 n} = \infty$
3. Limit $\infty$ means $\Omega$
4. So $n^{1.01} \in \Omega(\log^2 n)$.

  - 1e

No. Because $n^{1/2}$, ${1/2}$ is a positive number, any positive polynomial outgrows any polylogarithmic function. Therefore $\sqrt{n} \notin O({log^3n})$

Proof by limit:

1. $\lim \frac{\sqrt{n}}{\log^3 n} = \lim \frac{n^{1/2}}{\log^3 n}$
2. Top is polynomial, bottom is polylog.
3. So the limit is $\infty$.
4. $\sqrt{n} \notin O(\log^3 n)$.

  - 1f

Yes. Similar to the answer before, $n^{1/2}$ outgrows $log^3n$. Therefore $\sqrt{n} \in \Omega({log^3n})$

Proof by limit:

1. Same limit as (1e).
2. $\lim \frac{\sqrt{n}}{\log^3 n} = \infty$.
3. Limit $\infty$ means $\Omega$.
4. $\sqrt{n} \in \Omega(\log^3 n)$.

  - 1g

Proof that $o(g) \cap \omega(g) = \emptyset$:

1. $f \in o(g)$ means $\lim \frac{f}{g} = 0$.
2. $f \in \omega(g)$ means $\lim \frac{f}{g} = \infty$.
3. One limit cannot be both $0$ and $\infty$.
4. So no such $f$ exists.
5. Hence the intersection is empty.

---

2. **SPARC to Python**

  - 2b

It is a recursive function that places the min value of both parameters as its first parameter and `max % min` as the second parameter, and at the end returns the greatest common divider of given two values a and b .

  - 2c

Work for `foo` can be calculated in return condition:

```python

def foo(a: int, b: int) -> int:
    # ...
    else:
        x, y = min(a, b), max(a, b)
        return foo(x, y % x) # <--- here
```

Let `W` be work of `foo`, we can say:
- For $a == 0$ or $b == 0$:
$$W(a, b) = O(1)$$
because:
```python
    if a == 0:
        return b
    elif b == 0:
        return a
```
- Else: 
$$W(a, b) = O(1) + W(min(a, b), max(a, b) \mod min(a, b))$$
because:
```python
        return foo(x, y % x)
```
We know $y = max(a, b)$ and $x = min(a, b)$:
$$W(a, b) = O(1) + W(x, y \mod x)$$
Because of the $mod$ we know that $W(a,b)$ shrinks exponentially. Meaning:
$$W(a, b) = O(\log y)$$

Because `foo` never branches to more than one children Span has to be the same as Work.
$$S(a, b) = W(a, b) = O(\log y)$$

3. **Parallelism and recursion**

  - 3b

  - 3d

  - 3e
