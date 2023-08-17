- **Lamda function** does not has a name, only used to return the values.
- it does not perform operations or actions, it just handles input and returns.
```py
add = lamda x,y : x+y

print(add(5,7))

(lamda x,y : x+y)(5+7)
```

- lamda function code to double the elements in a list
```py
sequence = [1, 3, 5, 9]

doubled = [(lamda x: x*2)(x) for x in sequence]

doubled = list(map(lamda x: x*2, sequence))
```