# useFech-react-hook
A react custom hook with the purpose of abstract all part of fetching data and treating return object of third party API.

A bunch of examples are available [here](https://github.com/PedroMarianoAlmeida/use-fetch-examples)

## How to use:

### Installation:
- Download **useFetch.js** file (do not clone the repository)
- Add it to your project
- Import in React Component that you will use the hook
**This repository  isn't a complete react app, you should add the JS file on your project**

### Declaring

Similar to useState hook:

`const [ answerHook, setConfiguration ] = useFetch(myConfiguration);`

- The first variable is the JSX element to insert in your render function
- The second variable is the function to update configuration, it needs a new configuration object as a parameter (this configuration object will be explained furder)
- The parameter of the hook is the initial configuration (same object informed above)

### Configuration Object

This object presents all information the hook needs to Fetch and treat data. It has a considerable number of properties, but each one has a closed scope and defined purpose, and to standardize the way to send and receive data from a 3rd party API. It can be a little complex in beginning but after a few tries, you will become an expert!

A configuração inicial é um objeto com os seguintes parâmetros (valores dos parâmetros são exemplos):

- `url: "my URL",` - Required: String with the URL that you want to consume the API (all address text until immediately before the parameters)

- `parameters : [ { "nomeParameter": "ValueParameter" } ],` - Optional: Parameters used in the query. Your format must be exactly like the example: An array with each element in a single parameter object.

- `shouldRun: true/false,` Optional: Boolean value witch set if the fetch should be executed or not (if find some problem in the configuration it is automatically set to false). If not informed will be set to true.

- `logResponses: true/false,` Optional: Boolean value witch ask the developer if the log messages should be showed (about relevant steps of the process), it is recommended the use while development and after everything goes find disable. If not informed will be set to true.

- `doWhenInactive: () => "",` Optional: Should be filled with a function that returns the JSX Element that should be exhibit when the hook is inactive (shouldRun = false). If not informed will be set to "".

- `doWhenFetching: () => () => <h6>...Loading</h6>,` Optional: Should be filled with a function that returns the JSX Element that should be exhibit when the hook is fethcing the data. If not informed will be set to "".

- `doWhenSuccess: (rawAnswer) => <h1> { rawAnswer.specificParam } </h1>,` Optional: Should be filled with a function that returns the JSX Element that should be exhibit when the data returns without errors from fetch. **Your argument is the return object**. If not informed will be set to "", but will generate a log informing that the data fetched will be not exhibited on screen, and set logResponse to true (this way the data is showed in the console at least)

- `doWhenFail: (errorName, errorMessage) => <h6> {errorMessage} </h6>` Optional: Should be filled with a function that returns the JSX Element that should be exhibit when the hook fails in fetching the data. Your arguments are the Name of the error and the message of the error. If not informed will be set to "".

- `errorAPIvalue:  [ "Response", "False", "Error"] ,` Optional: Sometimes the return of API is an Error itself, despite the Fetch was succeded (because it returns an object, but not the expected one). So this property is used to identify these cases and treated them like errors. Your format is an array with 3 values: The name of propriety in the object who contains the error information, the second is the value of that propriety and the last is the propriety who contains the error message. If not informed is assumed that all return of API is valid.

### Other exemples

- [Movie Finder](https://github.com/PedroMarianoAlmeida/movie-finder-porfolio) - See components **[ListMoviesFounded.js](https://github.com/PedroMarianoAlmeida/movie-finder-porfolio/blob/master/src/components/HomePage/ListMoviesFounded.js)** and **[MovieDetails.js](https://github.com/PedroMarianoAlmeida/movie-finder-porfolio/blob/master/src/components/MovieDetails.js)**


