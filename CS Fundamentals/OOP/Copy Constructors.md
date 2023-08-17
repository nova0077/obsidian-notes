# COPY CONSTRUCTOR
- COPY => when we want to assign an existing object data to a new object of the same class.
- This can be done by 2 methods
	1. Copy constructor
	2. Implicit Copy or Assignment Operator
```cpp
#include<bits/stdc++.h>
using namespace std;

class Num{
public:
	int a;
	Num(){}
	// copy constructor
	Num(Num &obj){
		cout<<"copy constructor called"<<endl;
		a = obj.a;
	}
};
int main()
{
	Num x;
	x.a = 6;
	Num y(x);
	cout<<"y => "<<y.a<<endl;
	
	Num z; // copy constructor wont be called
	z = y; // copy Assignment operator is called
	cout<<"z => "<<z.a<<endl;
	
	Num z1 = y; // copy constructor called
	cout<<"z1 => "<<z1.a;
}
/* OUTPUT
copy constructor called
y => 6
z => 6
copy constructor called
z1 => 6
*/
```
 
## DEFAULT COPY
- Default Copying typically refers to how objects are copied when assignment operations are performed
- When you perform a simple assignment (`=`) or use a copying function **shallow copy** of the object is created by default.

## SHALLOW COPY
- Creating copy of object by copying data of all member variables as it is.
- Shallow copy also copies the pointer memory address to the new object, that means both the objects pointers are pointing to a same address.
- Change in the copied object will also be reflected in the original object
## DEEP COPY
- Creating an object by copying data of another object along with the values of memory resources resides outside the object but handled by that object.
- It creates a separate memory address for pointers and set values 

```cpp
class Dummy
{
private:
	int a,b;
	int *p;
public:
	Dummy()
	{
		p = new int;
	}
	// Shallow copy constructor
	Dummy (Dummy &d)
	{
		a=d.a, b=d.b, p=d.p;
	}
	// Deep copy constructor
	Dummy (Dummy &d)
	{
		a=d.a, b=d.b;
		p = new int;
		*p = *(d.p);
	}
	void setData(int x, int y, int z)
	{
		a=x, b=y, *p=z;
	}
	~Dummy()
	{
		delete_p;
	}
	// If we use shallow copy, then if we delete any single object, 
	// this leads to deletion of the memory block that are also being 
	// reffered by other objects.
};

int main()
{
	Dummy d1;
	d1.setData(3,4,5);
	
	Dummy d2=d1;
	d2.showData();
}
```

>[!note]
>When you have pointers members inside a class, it is better to use DEEP COPY instead of SHALLOW COPY

