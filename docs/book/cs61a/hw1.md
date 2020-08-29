
# Homework 1: Control

## Q1: Syllabus Quiz

[教学大纲](https://cs61a.org/articles/about.html)了解程度测试。（略）

## Q2: A Plus Abs B

原有代码不能修改，也就是只能在代码的基础上添加内容。

```python
def a_plus_abs_b(a, b):
    """Return a+abs(b), but without calling abs.

    >>> a_plus_abs_b(2, 3)
    5
    >>> a_plus_abs_b(2, -3)
    5
    >>> # a check that you didn't change the return statement!
    >>> import inspect, re
    >>> re.findall(r'^\s*(return .*)', inspect.getsource(a_plus_abs_b), re.M)
    ['return h(a, b)']
    """
    if b >= 0:
        h = add
    else:
        h = sub
    return h(a, b)

```

```python
$ python3 ok -q a_plus_abs_b
=====================================================================
Assignment: Homework 1
OK, version v1.15.0
=====================================================================

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Running tests

---------------------------------------------------------------------
Test summary
    1 test cases passed! No cases failed.
```

## Q3: Two of Three

注意，只能写一行代码！

```python
def two_of_three(x, y, z):
    """Return a*a + b*b, where a and b are the two smallest members of the
    positive numbers x, y, and z.

    >>> two_of_three(1, 2, 3)
    5
    >>> two_of_three(5, 3, 1)
    10
    >>> two_of_three(10, 2, 8)
    68
    >>> two_of_three(5, 5, 5)
    50
    >>> # check that your code consists of nothing but an expression (this docstring)
    >>> # a return statement
    >>> import inspect, ast
    >>> [type(x).__name__ for x in ast.parse(inspect.getsource(two_of_three)).body[0].body]
    ['Expr', 'Return']
    """
    return x**2 + y**2 + z**2 - max(x,y,z)**2
```

测试结果：

```python
$ python3 ok -q two_of_three
=====================================================================
Assignment: Homework 1
OK, version v1.15.0
=====================================================================

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Running tests

---------------------------------------------------------------------
Test summary
    1 test cases passed! No cases failed.
```

## Q4: Largest Factor



```python
def largest_factor(x):
    """Return the largest factor of x that is smaller than x.

    >>> largest_factor(15) # factors are 1, 3, 5
    5
    >>> largest_factor(80) # factors are 1, 2, 4, 5, 8, 10, 16, 20, 40
    40
    >>> largest_factor(13) # factor is 1 since 13 is prime
    1
    """
    "*** YOUR CODE HERE ***"
    f = x - 1
    while f > 0:
        if x % f == 0:
            return f
        f -= 1
```

```python
$ python3 ok -q largest_factor
=====================================================================
Assignment: Homework 1
OK, version v1.15.0
=====================================================================

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Running tests

---------------------------------------------------------------------
Test summary
    1 test cases passed! No cases failed.
```

## Q5: If Function vs Statement



## Q6: Hailstone

```python
def hailstone(x):
    """Print the hailstone sequence starting at x and return its
    length.

    >>> a = hailstone(10)
    10
    5
    16
    8
    4
    2
    1
    >>> a
    7
    """
    "*** YOUR CODE HERE ***"
    length = 1
    while x != 1:
        print(x)
        if x % 2 == 0:
            x //=  2    
        else:
            x = 3 * x + 1
        length = length + 1
    print(x)            
    return length
```

```python
$ python3 ok -q hailstone
=====================================================================
Assignment: Homework 1
OK, version v1.15.0
=====================================================================

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Running tests

---------------------------------------------------------------------
Test summary
    1 test cases passed! No cases failed.
```