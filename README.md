
# <p style="text-align: center;" align="center">konfiger</p>

<p style="text-align: center;" align="center">The parent repository for this organisation, Contains list of implemented functions. </p>

## Table of content
- [Implemented Functions](#implemented-functions)
   - [Saving](#saving)
- [TODOD](#todos)
- [How it works](#how-it-works)
- [Contributing](#contributing)
- [Support](#support)
- [License](#license)

## Implemented Functions

The key `k` must always be string, the `v` can be any type but the String 
value will be saved and when requested the value returned by default is the 
String value else requested with a typed get e.g. `getBoolean` then the 
value will be converted to a valid `boolean` in the language.  

### Saving

| Function        | Usage         
| --------------- | ------------- 
| put(k, v)           | Put any object into the konfiger the value `v` string value will be saved, the key `k` must be string 
| putString(k, v)           | Put a String `v` into the konfiger


putString()

## TODOS

 - [ ] create website with reStructureText
 - [ ] write several example in the documentation 
 - [ ] examples to load and save locally in each languages
 - [x] implements size() method in all the languages
 - [x] implements clear() method in all the languages
 - [x] implemets isEmpty() method in all the languages
 - [ ] enable cacheing in the konfiger
 - [ ] When commiting other language must include name in the LICENCE as `Copyright (c) {Year} {Name}:konfiger` confirm
 - [ ] When commiting other language author should include paypal or patreon link

## How it works

KonfigerObject class contains the key and value field and the fields setter and getter. The KonfigerObject is the main internal type used in the Konfiger class.
 
In Konfiger the key value pair is stored in `Array[]` type, all search updating and removal is done on the `konfigerObjects` in the class. The string sent as first parameter if parsed into valid key value using the separator and delimiter fields. The `toString` method also parse the `keyValueObjects` content into a valid string with regards to the 
separator and delimeter. 

The `open` function reloads the file from disk to update the `Konfiger` if changes is written to the file in another program, if the file does not exist `FileNotSpecified` exception is thrown if `errTolerance` is set to false. The `save` function write the current `Konfiger` to the file, if the file does not exist is is created if it can. If no file is specified on init everything is written in memory and is disposed on app exit.

## Contributing

Before you begin contribution please read the contribution guide at [CONTRIBUTING GUIDE](https://github.com/konfiger/konfiger.github.io/CONTRIBUTING.MD)

You can open issue or file a request that only address problems in this implementation on this repo, if the issue address the concepts of the package then create an issue or rfc [here](https://github.com/konfiger/konfiger.github.io/)

## Support

You can support some of this community as they make big impact in the developement of people to get started with software engineering.

- https://www.patreon.com/devcareer

## License

MIT License Copyright (c) 2019 Adewale Azeez - konfiger



