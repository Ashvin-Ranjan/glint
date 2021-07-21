# Maintaining GLINT

## Using N

GLINT is written in N, a strongly typed language that can run on mac or windows. Here is the [main repo for N](https://github.com/nbuilding/N-lang) and the [documentation for it](https://nbuilding.github.io/N-lang-docs). GLINT is currently written for `v1.3.1` of N.

## How GLINT works

GLINT is broken down into two main parts, getting data (Marked by the loading bar) and opening the http server (Marked by the http server logs coming through)

### Getting the data

The first part GLINT will be using the GitHub API to get the pull request data for the repo and compiling the reviewers into a json format, you will notice a lot of `if let` statements, here is why:

Most response data in N for http is dealt in `json` format, json formatting is an enum that goes as follows:
```js
type pub value = <object map[str, value]>
               | <number float>
               | <string str>
               | <boolean bool>
               | null
```

This means that the data has to be destructured and at the time of writing this requires `if let` to do it in the most efficient way.

The end goal of this process is to fit the data down into a `map[str, { timesRequested: int; timesResponded: int; averageResponseTime: int }`

### Opening the server

`http` servers in N are quite low-level and take in two parts:
- The port to open to (`int`)
- A function that takes in the path, request type, and header and additional data and returns a `cmd[{ responseCode:int; data:list[int]; headers:map[str, str]; mimetype:str }]` (`str -> str -> json.value -> cmd[{ responseCode:int; data:list[int]; headers:map[str, str]; mimetype:str }]`)

GLINT ignores the request type and the header data and only cares about the `path`, if the path is `data` then it gives back the json data that it got, if it is anything else it loads up the `template.html` file and sends it through.

## utils.n

`utils.n` is filled with any other helper functions that will be used in `glint.n`:
- `parseConfig`: Parses the data given from `json.parse` into a config that `glint.n` can use (`json.value -> configData`)
- `reviewDataToJson`: Takes the data created in the first step of GLINT and converts it into a json for ease of use (`map[str, reviewData -> json.value]`)
- `convertTextToBytes`: Takes in a string and converts it into a list of bytes for the http server (`str -> list[int]`)
- `multString`: Takes in a string and repeats it(`int -> str -> str`)
- `getUserTeam`: Takes in a user login and a `list[(str, list[str])]` and sees which teams the user is in (`str -> list[(str, list[str])] -> list[str]`)

## Maintaining compatibility

N will try to maintain backwards compatibility, but if it does not work please install the current version of N that is supported for this project.

## Maintaining this doc

Please update this doc whenever new parts are added to any of the files and whenever N is updated, please also update [version support](./versionsupport.md).