```cpp
class A{
public:
	void f1(){}
	void f2(){}
};
class B:public A{
	void f1(){} // Method overriding
	void f2(int x){} // Method  Hiding
};

int main()
{
	B obj;
	obj.f1(); // B class is binded
	obj.f2(); // error
	obj.f2(4); // B class is binded 
}
```