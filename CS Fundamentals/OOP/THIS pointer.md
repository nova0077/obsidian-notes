- **Object Pointer** => A pointer which contains address of an object is called Object pointer.
- This is a local object pointer in every instance member function containing address of the caller object.
```cpp
class Box{
private:
	int l,b,h;
public:
	void setDimensions(int l, int b, int h){
		this->l=l;
		this->b=b;
		this->h=h;
	}
	void showDimensions(){
		cout<<l<<" "<<b<<" "<<h<<endl;	
	}
}
```