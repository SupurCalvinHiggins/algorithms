# 📚 Stack

## Interface

`stack` is an abstract data type that maintains an ordered collection of items.&#x20;

```cpp
template <typename T>
class stack {
public:
    void push(T val);
    void pop();
    T top();
    bool empty();
}
```

Items are added to the `stack` with the `push` method. The most recently added item (that still exists in the `stack`) is returned by the `top` method and removed from the `stack` by the `pop` method. This enforces a **Last-In First-Out** or **LIFO** order.&#x20;

<figure><img src=".gitbook/assets/image-from-rawpixel-id-6436496-original (1).png" alt="" width="375"><figcaption><p>A stack of books!</p></figcaption></figure>

`stack` works like a stack of books. Consider the image above.The yellow book can be inspected (`top`), removed (`pop`) or covered with a new book (`push`).  The  other books cannot be accessed without first removing the yellow book. That is, the  I LO order is enforced.&#x20;

## Implementation

Stacks are often implemented with dynamic arrays. Such implementations have $$\Theta(1)$$ amortized complexity for `push` and `pop` and $$\Theta(1)$$ complexity for `top`.

```cpp
template <typename T>
class stack {
private:
    vector<T> v;
public:
    void push(T val) { v.push_back(val); }
    void pop() { v.pop_back(); }
    T top() { return v.back(); }
    bool empty() { return v.empty(); }
}
```

However, some variations are possible. A linked list can be used when amoritized bounds are unacceptable.

```cpp
template <typename T>
class stack {
private:
    forward_list<T> l;
public:
    void push(T val) { l.push_front(val); }
    void pop() { l.pop_front(); }
    T top() { return l.front(); }
    bool empty() { return l.empty(); }
}
```

A static array can be used when the maximum number of items is known ahead of time.

## Algorithms
