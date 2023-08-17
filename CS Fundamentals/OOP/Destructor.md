- Destructor is an instance member function of a class
- The name of the destructor is same as the name of a class but preceded by tilde (~) symbol.
- Destructors can never be static
- Destructor has no return type
- Destructor takes no argument (No overloading is possible).
- It is invoked implicitly when object is going to destroy.
>[!important]
>- Destructor does not destroy an object, Destructor is called when we want to destroy an object.
>- It is the last function of an object

```cpp
#include<bits/stdc++.h>
using namespace std;

class Complex{
private:
	int a,b;
	int *p
public:
	// Constructor
	Complex(){
		p = new int;
	}
	// Destructor
	~Complex(){
		cout<<"Destructor is called";
		delete(p);
		// After deleting the obj, we cannot deallocate memory of the pointer pointing by the p.
	}
}
void func()
{
	Complex obj;
}
int main()
{
	func();
}
```

Explanation: 
In the main function, "func" is called, in which we are initialising an object.
When the function call is over the destructor is called. 