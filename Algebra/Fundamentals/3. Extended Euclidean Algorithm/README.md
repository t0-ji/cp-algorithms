# Extended Euclidean Algorithm
## Introduction
While the Euclidean Algorithm calculates only the GCD of two integers `a` and `b`, the the extended version also calculates such coefficients `x` and `y` for which:
<pre>a * x + b * y = gcd(a, b)</pre>

## Algorithm
Lets denote `gcd(a, b)` with `g` : <pre>a * x + b * y = g</pre>
If we recall the Euclidean Algorithm, 

<pre>
gcd(a, b) = a                If b == 0
          = gcd(b, a mod b)  Otherwise
</pre>
We can see that the algorithm ends with `b == 0` and `a = g`.

With this information we can easily find the value of the equation, <br>`a * x + b * y = g` :
<pre>g * 1 + 0 * 0 = g</pre>
Starting from these coefficients `(x, y) = (1, 0)` , we can go backwards up the recursive calls.

All we need to do is to figure out how the coefficients `x` and `y` change during the transition from `(a, b)` to `(b, a mod b)` .

Let us assume we found the coefficients _(x<sub>1</sub>, y<sub>1</sub>)_ for `(b, a mod b)` :
<pre>
b * x<sub>1</sub> + (a mod b) * y<sub>1</sub> = g
</pre>
```c++
/* c++ */
int gcd (int a, int b) {
    if (b == 0)
        return a;
    else
        return gcd (b, a % b);
}
```
```py
# Python
def gcd(a, b):
    if b == 0:
        return a
    else:
        return gcd(b, a % b)
```