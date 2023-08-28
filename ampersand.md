# What does '&' mean in C++

During a discussion with a co-worker the talk fell onto the humble &. What does it mean in C++? How many meanings are there of the character, how does this affect teaching C++?


## Lets get the obvious out of the way...

There's two main groups of use cases, a single ampersand (&) and two consecutively (&&). These does of course have very distinct meanings, but also overlap in certain situations.

I'll begin by mentioning the basic use cases of both.

### Basic usage of a single &

Using it to get the address of an lvalue.
```
int i{12};
int *i_ptr = &i;
```

It can be used to pass something by reference to a function.
``` 
f(int&);
```

It can be used to create a refence to a value.
```
int& i_ref = i;
```

It can be used to bitwise __and__ two values.

```
uint8_t val = 0b0100'0010 & 0b1111'1111;
```



### Basic usage of &&

It can be used to logical __and__ two values.

```
bool b = true && false;
```
It can be used to pass something by rvalue to a function.
``` 
f(int&&);
```





## Templates
```
template<typename T>
void f1(T&&);
```

The same as.
```
void f2(auto&&);
```


```
auto&& i = f3();
```

## Lambda captures
```
int i{0};
auto l = [&]{ return ++i; };
auto l2 = [&i]{ return ++i; };
```

## Type of this

```
struct S {
    void lvalueref() &;
    void rvalueref() &&;
};
```

