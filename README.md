# use-fetch-react

#### Demo
[Codesandbox link](https://codesandbox.io/s/winter-star-hpcyp?fontsize=14&hidenavigation=1&theme=dark)


### Installation
`yarn add use-fetch-react`

### Usage
#### Basic example

```
import React from "react";
import useFetch from "use-fetch-react";

export default function App() {
  const [executeFetch, { data, error, loading, called }] = useFetch(`https://swapi.co/api/people`);

  !called && executeFetch();

  console.log({ data, error, loading, called });
  return (
    <div className="App">
      <button onClick={executeFetch}>Refresh</button>
      {error && <p>{error.message}</p>}
      {loading && <p>loading...</p>}
      {data &&
        data.results &&
        data.results.map(({ name, gender, mass, height }, index) => (
          <div key={index}>
            {name} {" - "}
            {gender} {mass}kg {height}cm
          </div>
        ))}
    </div>
  );
}
```

#### More options

```
 const [executeFetch, { data, error, loading, called }] = useFetch(
    `https://swapi.co/api/people`,
    {
      method: 'POST', // *GET, POST, PUT, DELETE, etc.
      headers: {
        authorization: `Bearer ${authToken}`,
        'Content-Type': 'application/json',
         // 'Content-Type': 'application/x-www-form-urlencoded',
      },
      body: data,
      onCompleted(res) {
        console.log(res);
      },
      onError(err) {
        console.log(err);
      }
    }
  );
```
