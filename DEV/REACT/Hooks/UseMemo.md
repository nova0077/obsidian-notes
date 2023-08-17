- It helps to optimise the performance by memoizing the result of a computation. 
- It allows us to avoid unnecessary recalculations of expensive operations when the inputs to those operations haven't changed.
```jsx
import axios from "axios";
import { useEffect, useState, useMemo } from "react";

export default function MemoTutorial() {
  const [data, setData] = useState(null);
  const [toggle, setToggle] = useState(false);

  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/comments")
      .then((response) => {
        setData(response.data);
      });
  }, []);

  const findLongestName = (comments) => {
    if (!comments) return null;
    
    let longestName = "";
    for (let i = 0; i < comments.length; i++) {
      let currentName = comments[i].name;
      if (currentName.length > longestName.length) {
        longestName = currentName;
      }
    }
    console.log("THIS WAS COMPUTED");
    return longestName;
  };

  const getLongestName = useMemo(() => findLongestName(data), [data]);

  return (
    <div className="App">
      <div> {getLongestName} </div>
      <button
        onClick={() => {
          setToggle(!toggle);
        }}
      >
        {" "}
        Toggle
      </button>
      {toggle && <h1> toggle </h1>}
    </div>
  );
}
```

1. In this above code, we are using a function "findLongestName" to find the longest name from the data which we are fetching from API.
2. But whenever we toggle the button, the entire code gets renders and it calculates the longest name function again.
3. By using useMemo Hook, the function will only runs when the dependencies get changed.
