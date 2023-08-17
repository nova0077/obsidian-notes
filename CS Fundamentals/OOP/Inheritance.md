- It is a process of inheriting properties and behaviours of existing class into a new class
- PRIVATE members of a class will also be inherited, but those are not accesible.
```cpp
// syntax
class Base_class
{

};
class Derived_calss: Visibility_mode Base_class
{

};
```

## PRIVATE INHERITANCE
```cpp
class Array{
private:
	int a[10];
public:
	void insert(int ind, int val)
	{
		a[ind]=val;
	}
};

class Stack: private Array{
	int top;
	public:
		void push(int val){
			insert(top, val);
		}
}

int main()
{
	Stack s1;
	s1.push(34);
	s1.insert(2,56); // will restrict
	// If we make public relationship, then we can directly insert val in arr 
	// to avoid this we use private or protected relationship.
}
```