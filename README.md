# use-fetch-react

#### Demo
[Codesandbox link](https://codesandbox.io/s/winter-star-hpcyp?fontsize=14&hidenavigation=1&theme=dark)


### Installation
`yarn add use-fetch-react`

### Usage

`import { useFetch } from "use-fetch-react"`
```
const Page = () => {
  const [request, { data, error, loading, called }] = useFetch(
    "https://swapi.co/api/people",
    {
      onCompleted(response) {
        console.log("onCompleted", response)
      },
      onError(err) {
        console.log("onError", err)
      },
    }
  )

  return (
    <>
      {!called && <p>Please press the fetch button</p>}
      {error && <ErrorMessage>{error.message}</ErrorMessage>}

      <Button
        loading={loading}
        onClick={request}
      >
        Fetch data
      </Button>
      
      {loading && (
        <div>
          <BarLoader />
        </div>
      )}

      {data &&
        data.results &&
        data.results.map((person, index) => {
          return <div key={index}>{person.name}</div>
        })}
    </>
  )
}
```
