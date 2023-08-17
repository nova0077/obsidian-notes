- Friend Function is not a member function of a class to which it is a friend.
- Friend function is declared in the class with friend keyword.
- It must be defined outside the class to which it is friend.
- Friend function can access any member of the class to which it is friend.
- Friend function cannot access members of the class directly.

```cpp
#include<bits/stdc++.h>
using namespace std;

class Complex{
	private:
		int a,b;
	public:
		void setData(int x, int y){
			a=x, b=y;
		}
		void showData(){
			cout<<a<<" "<<b<<endl;
		}
		friend void func(Complex);
};

void func(Complex c)
{
	cout<<"sum is "<<c.a+c.b<<endl;
}

int main()
{
	Complex c1, c2, c3;
	c1.setData();
	func(c1);
}
```

- Friend function can become friend to more than one class
- Friend function can be private or public, it does not matter because friend function is not a member function. 

```cpp
class B; // forward declaration of class B to avoid compilation errors
class A{
private:
	int a;
	friend void func(A, B);
};

class B{
private:
	int b;
	friend void func(A, B)
};

void func(A ob1, B ob2)
{
	cout<<"sum is "<<o1.a+o2.b<<endl;
}
int main()
{
	A obj1;
	B obj2;
	func(obj1, obj2);
}
```

## Operator Overloading in Friend function

```cpp
#include<bits/stdc++.h>
using namespace std;

class Complex{
private:
	int a,b;
public:
	void setData(int x, int y){
		a=x, b=y;
	}
	void showData(){
		cout<<a<<" "<<b<<endl;
	}
	friend Complex operator+(Complex, Complex);
};

Complex operator+(Complex X, Complex Y){
	Complex temp;
	temp.a = X.a + Y.a;
	temp.b = X.b + Y.b;
	return (temp);
}
int main()
{
	Complex c1, c2, c3;
	c1.setData(3,4);
	c2.setData(5,6);
	c3 = c1+c2; // c3 = operator+(c1, c2);
	c3.showData();
}
```

- Member function of one class can become friend to another class

```cpp
#include<bits/stdc++.h>
using namespace std;
class A
{
	public:
	void func()
	{}
	void foo()
	{}
};
class B
{
	friend void A::fun();
	// if you want to make all the functions of A class friend functions of B
	friend class A;
}
```

