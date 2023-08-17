- A class containing pure virtual function is an abstract class
- We cannot instantiate abstract class
```cpp
class Person
{
	public:
		virtual void func() = 0; // pure virtual function
		void f1()
		{}
};
class Student: public Person
{
	public:
		void func(){
			
		}
};

```