- When an operator is overloaded with multiple jobs, it is known as operator overloading.
- It is a way to implement POLYMORPHISM

```cpp
class Complex
{
	private:
		int a,b;
	public:
		void setData(int x, int y){
			a=x, b=y;
		}
		void showDate(){
			cout<<a<<" "<<b<<endl;
		}
		Complex operator +(Complex c) // binary operator
		{
			Complex temp;
			temp.a = a+c.a;
			temp.b = b+c.b;
			return (temp)
		}
		Complex operator -() // uniary operator
		{
			Complex temp;
			temp.a = -a;
			temp.b = -b;
			return temp;
		}
};

int main()
{
	Complex c1,c2,c3;
	c1.setData(3, 4);
	c2.setData(5, 6);
	c3 = c1 + c2 
	// c3 = c1.operator+(c2)
	c2=-c1;
	// c2 = c1.operator-();
}
```

## PRE and POST Increment Overloading
```cpp
#include<bits/stdc++.h>
using namespace std;
class Integer{
	private:
		int x;
	public:
		void setData(int a){
			x=a;
		}
		void showData(){
			cout<<x<<endl;
		}
		//PRE INCREMENT 
		Integer operator ++(){
			Integer i;
			i.x = ++x;
			return i;
		}
		// POST INCREMENT
		Integer operator++(int){
			Integer i;
			i.x = x;
			x++;
			return x;
		}
};

int main()
{
	Integer i1, i2;
	i1.setData(3);
	i1.showData();
	i2 = ++i1; // i2=i1.operator++();
	// i2 = i1++; calls same function ++ operator if we doesnot write post increment function.

	i2 = i1++;  
}
```