# Python-Learning-Code
## 2018/10/16


```python
abs(100)
```




    100




```python
abs(-20)
```




    20




```python
help(isinstance)
```

    Help on built-in function isinstance in module builtins:
    
    isinstance(obj, class_or_tuple, /)
        Return whether an object is an instance of a class or of a subclass thereof.
        
        A tuple, as in ``isinstance(x, (A, B, ...))``, may be given as the target to
        check against. This is equivalent to ``isinstance(x, A) or isinstance(x, B)
        or ...`` etc.
    
    


```python
isinstance(abs(10), float)
```




    False




```python
import math

def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny
```


```python
r =  move(100, 100, 60, math.pi/6)
print(r)
print(r[0])
print(r[1])
```

    (151.96152422706632, 70.0)
    151.96152422706632
    70.0
    

### 计算一个一元二次方程的解的情况


```python
def quadratic(a, b, c):
    type_a = isinstance(a, (int, float))
    type_b = isinstance(b, (int, float))
    type_c = isinstance(c, (int, float))
    if type_a & type_b & type_c:
        print("show time")
        delta = b*b - 4* a * c
        if delta < 0:
            print('无解')
        elif delta == 0:
            print("只有一个解")
            result = -b / (2*a)
            print("该解为：%d" %result)
        else:
            print("该方程有两个解")
            result_one = (-b + math.sqrt(delta))/(2*a)
            print("第一个解为：%s" %result_one)
            result_two = (-b - math.sqrt(delta))/(2*a)
            print("第一个解为：%s" %result_two)
    else:
        print("输出的数据类型有问题，请重新输入")
```


```python
a = 1
b = 4
c = 1
quadratic(a, b, c)
```

    show time
    该方程有两个解
    第一个解为：-0.2679491924311228
    第一个解为：-3.732050807568877
    

### 注册问题



```python
def Enroll(name, age, sex="male"):
    print("name: %s" %name)
    print("age: %s" %age)
    print("sex: %s" %sex)
```


```python
Enroll("xiaofei", 18)
```

    name: xiaofei
    age: 18
    sex: male
    


```python
def calc(*numbers):
    print(type(numbers))
    sum = 0
    print(numbers)
    for ind, con in  enumerate(numbers):
        print(ind)
        sum = sum + con * con
    return sum
```


```python
nums = [1, 3, 3]
calc(*nums)
```

    <class 'tuple'>
    (1, 3, 3)
    0
    1
    2
    




    19




```python
def nub(*number):
    print(number)
    
```


```python
def person(name, age, **kw):
    print("name:", name, "age:", age, "rest:", kw )
    if 'sex' in kw:
        print('we have sex')
    if 'city' in kw:
        print('we have city')
```


```python
person("xiaofei", 12)
```

    name: xiaofei age: 12 rest: {}
    


```python
person("xiaoyao", 12, sex='female')
```

    name: xiaoyao age: 12 rest: {'sex': 'female'}
    we have sex
    

### 关键字参数的调用形式


```python
person("huanhuan", 14, China) #调用的时候，应该使用键值的形式， key=value, 或者 **dict的形式
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-10-19e6a1b1808b> in <module>()
    ----> 1 person("huanhuan", 14, China) #调用的时候，应该使用键值的形式， key=value
    

    NameError: name 'China' is not defined



```python
other_message = {'city': 'China', 'sex': "male"}
person('xiaokeai', 18, **other_message)
```

    name: xiaokeai age: 18 rest: {'city': 'China', 'sex': 'male'}
    

### 强制关键字的定义


```python
def person(name, age, *, city, job):
    print(name, age, city, job)
```


```python
person('Jack', 24, city='Beijing', job='Engineer')
```

    Jack 24 Beijing Engineer
    

### 强制关键字的调用


```python
person('Jack', 24, )
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-21-c3c80b42e32c> in <module>()
    ----> 1 person('Jack', 24, )
    

    TypeError: person() missing 2 required keyword-only arguments: 'city' and 'job'


### 计算多个数的乘积


```python
def product(*numbers):
    result = 1
    for ind, con in enumerate(numbers):
        result = result * con
    print("这次计算的是%s个数的乘积，答案为%s" %(len(numbers), result))
    return result
```


```python
product(1, 2, 3, 5, 5,6, 9)
```

    这次计算的是7个数的乘积，答案为8100
    




    8100



### 汉诺塔问题


```python
def  hannoi(n, a, b, c):
    if n==1:
        print(a, '-->', c)
    else:
        hannoi(n-1, a, c, b)
        print(a, '-->', c)
        hannoi(n-1, b, a, c)
```


```python
hannoi(3, 'A', 'B', 'C')
```

    A --> C
    A --> B
    C --> B
    A --> C
    B --> A
    B --> C
    A --> C
    


```python

```
