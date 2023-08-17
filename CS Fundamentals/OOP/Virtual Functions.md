- We cant able to do method overriding, when we use pointer of parent class to represent child class. And call the overriden function of the child class due to early binding .
- To avoid this we use late binding by making the function virtual.

```cpp
class A
{
public:
	virtual void f1(){}
};
class B: public A
{
public:
	void f1(){} // function overriding
}
```