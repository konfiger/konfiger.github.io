# {::nomarkdown}<p style="text-align: center;" align="center"><img src="https://github.com/konfiger/konfiger.github.io/raw/master/icons/konfiger.png" alt="konfiger" style="width:180px;height:160px;" width="180" height="160" /><br /> konfiger</p>{:/}

<p style="text-align: center;" align="center">The parent repository for this organisation, Contains list of implementations and functions frame.</p>

This project is the closest thing to Android [Shared Preference](https://developer.android.com/reference/android/content/SharedPreferences) in other languages and off the Android platform.

## The Implementation Languages

| Language        | Links         
| --------------- | ------------- 
| NodeJS           | [documentation](https://konfiger.github.io/konfiger-nodejs)
|            | [npm](https://www.npmjs.com/package/konfiger)
|            | [source](https://github.com/konfiger/konfiger-nodejs)
|            | [examples](https://github.com/konfiger/konfiger.github.io/blob/master/usecases/use_cases.js.md)
| - | -
| Java           | [documentation](https://konfiger.github.io/konfiger-java)
|            | [source](https://github.com/konfiger/konfiger-java)
|            | [examples](https://github.com/konfiger/konfiger.github.io/blob/master/usecases/use_cases.java.md)
| - | -
| C           | [documentation](https://konfiger.github.io/konfiger-c)
|            | [source](https://github.com/konfiger/konfiger-c)
|            | [examples](https://github.com/konfiger/konfiger.github.io/blob/master/usecases/use_cases.c.md)
| - | -
| Python           | [documentation](https://konfiger.github.io/konfiger-python)
|            | [pip](#)
|            | [source](https://github.com/konfiger/konfiger-python)
|            | [examples](https://github.com/konfiger/konfiger.github.io/blob/master/usecases/use_cases.python.md)
| - | -
| C Sharp           | [documentation](https://konfiger.github.io/konfiger-csharp)
|            | [nuget](#)
|            | [source](https://github.com/konfiger/konfiger-csharp)
|            | [examples](https://github.com/konfiger/konfiger.github.io/blob/master/usecases/use_cases.csharp.md)
| - | -
| Rust           | [documentation](https://konfiger.github.io/konfiger-rust)
|            | [source](https://github.com/konfiger/konfiger-rust)
|            | [examples](https://github.com/konfiger/konfiger.github.io/blob/master/usecases/use_cases.rust.md)
| - | -
| C++           | [documentation](https://konfiger.github.io/konfiger-cpp)
|            | [source](https://github.com/konfiger/konfiger-cpp)
|            | [examples](https://github.com/konfiger/konfiger.github.io/blob/master/usecases/use_cases.cpp.md)
| - | -
| Dart           | [documentation](https://konfiger.github.io/konfiger-dart)
|            | [source](https://github.com/konfiger/konfiger-dart)
|            | [examples](https://github.com/konfiger/konfiger.github.io/blob/master/usecases/use_cases.dart.md)
| - | -
| Ring           | [documentation](https://konfiger.github.io/konfiger-ring)
|            | [source](https://github.com/konfiger/konfiger-ring)
|            | [examples](https://github.com/konfiger/konfiger.github.io/blob/master/usecases/use_cases.ring.md)
| - | -
| Powershell           | [documentation](https://konfiger.github.io/konfiger-powershell)
|            | [source](https://github.com/konfiger/konfiger-powershell)
|            | [examples](https://github.com/konfiger/konfiger.github.io/blob/master/usecases/use_cases.powershell.md)

## Contributors

 - [Adewale Azeez](https://twitter.com/iamthecarisma)

## Table of content
- [The Implementation Languages](#the-implementation-languages)
- [Contributors](#contributors)
- [Documentation Brief](#documentation-brief)
   - [KonfigerStream](#konfigerstream)
      - [KonfigerStream Constructors](#konfigerstream-constructors)
      - [Methods](#methods)
   - [Konfiger](#konfiger)
      - [Konfiger Constructors](#konfiger-constructors)
      - [Public Fields](#public-fields)
      - [Putting](#putting)
      - [Getting](#getting)
      - [Removing](#removing)
      - [Read and Write](#read-and-write)
      - [Delimeter and Seperator](#delimeter-and-seperator)
      - [Others](#others)
- [TODOS](#todos)
- [How it works](#how-it-works)
- [Contributing](#contributing)
- [Support](#support)
- [License](#license)

## Documentation Brief

### KonfigerStream

#### KonfigerStream Constructors

| Function        | Description         
| --------------- | ------------- 
| fileStream(String, Char, Char, Boolean)   | Set the KonfigerStream file path, this cannot be changed, the last parameter is boolean if true the stream is error tolerant and does not throw any exception on invalid entry, only the first parameter is cumpulsory
| stringStream(String, Char, Char, Boolean)   | Set the KonfigerStream string value, this cannot be changed, the second param is the delimeter and the third param is the seperator, the last parameter is boolean if true the stream is error tolerant and does not throw any exception on invalid entry, only the first parameter is cumpulsory

#### Methods

| Function        | Description         
| --------------- | ------------- 
| hasNext() | Check if the KonfigerStream has another KonfigerObject in it before reading 
| next() | The current KonfigerObjeect in the stream
| validateFileExistence(String) | Validate the specified parameter (filePath) exists on the FileSystem

### Konfiger

The Key must always be string, the Value can be any type but the String 
value will be saved and when requested the value returned by default is the 
String value else requested with a typed get e.g. `getBoolean` then the 
value will be converted to a valid `boolean` in the language.  

#### Konfiger Constructors

| Function        | Description         
| --------------- | ------------- 
| fromFile(String, Boolean)           | Load the configer datas from a file, the first parameter is the file path, the second boolean parameter indicates whether to read all the entry in the file in the constructor or when needed, the default delimeter(`=`) and seperator(`\n`) will be used
| fromFile(String, Boolean, Char, Char)           | Load the configer datas from a file, the first parameter is the file path, the second boolean parameter indicates whether to read all the entry in the file in the constructor or when needed, the third param is the delimeter and the fourth param is the seperator
| fromString(String, Boolean)           | Load the configer datas from a file, the first parameter is the String(can be empty), the second boolean parameter indicates whether to read all the entry in the file in the constructor or when needed, the default delimeter(`=`) and seperator(`\n`) will be used
| fromString(String, Boolean, Char, Char)           | Load the configer datas from a file, the first parameter is the String(can be empty), the second boolean parameter indicates whether to read all the entry in the file in the constructor or when needed, the third param is the delimeter and the fourth param is the seperator
| fromStream(KonfigerStream, Boolean)           | Load the configer datas from a KonfigerStream object, the second boolean parameter indicates whether to read all the entry in the file in the constructor or when needed this make data loading progressive as data is only loaded from the file when put or get until the Stream reaches EOF


#### Public Fields

| Function        | Description         
| --------------- | ------------- 
| MAX_CAPACITY           | The number of datas the konfiger can take, 10000000


#### Putting

The `put` functions also update the value at the location if it already in the konfiger

| Function        | Description         
| --------------- | ------------- 
| put(String, Object)           | Put any object into the konfiger the Object value string value will be saved
| putString(String, String)           | Put a String into the konfiger
| putBoolean(String, Boolean)           | Put a Boolean` into the konfiger
| putLong(String, Long)           | Put a Long into the konfiger
| putInt(String, int)           | Put a Int into the konfiger
| putFloat(String, Float)           | Put a Float into the konfiger

#### Getting

| Function        | Description         
| --------------- | ------------- 
| keys()           | Get all the keys entrie in the konfiger 
| values()           | Get all the values entrie in the konfiger 
| entries()           | Get all the entries in the konfiger in a `Map<K, V>`
| get(String, Any)       | Get a value as string, if the key does not exist the seconds parameter will be returned
| getString(String, String)   | Get a value as string, if the key does not exist the second parameter is returned
| getBoolean(String, Boolean)   | Get a value as boolean, if the key does not exist the second parameter is returned
| getLong(String, Long)   | Get a value as long, if the key does not exist the second parameter is returned
| getInt(String, Int)   | Get a value as int, if the key does not exist the second parameter is returned
| getFloat(String, Float)   | Get a value as float, if the key does not exist the second parameter is returned


#### Removing

| Function        | Description         
| --------------- | ------------- 
| remove(int)           | Remove the entry at a particular index
| remove(String)           | Remove the entry using the data Key 

#### Read and Write

| Function        | Description         
| --------------- | ------------- 
| appendString(String)          | Append new data to the konfiger from a string, the new string delimeter and seperator must be the same with the current konfigure delimeter and seperator
| appendFile(String)          | Read new datas from the file path and append, the new file delimeter and seperator must be the same with the current konfigure delimeter and seperator
| save(String?)         | Save the konfiger datas into it IO path if specified, if no IO path specifed in the parameter the file path used in constructor is used, this does not clear the data

#### Delimeter and Seperator

| Function        | Description         
| --------------- | ------------- 
| getSeperator()           | Get seperator char that seperate the datas
| getDelimeter()           | Get delimeter char that seperated the key from object
| setSeperator(Char)           | Change seperator char that seperate the datas, note that the file is not updates, to change the file call the `save()` function
| setDelimeter(Char)           | Change delimeter char that seperated the key from object, note that the file is not updates, to change the file call the `save()` function

#### Others

| Function        | Description         
| --------------- | ------------- 
| size()           | Get the total size of datas in the konfiger
| clear()           | clear all the datas in the konfiger. if the konfiger is attached to a file, the file is updated immediatly 
| isEmpty()           | Check if the konfiger does not have an data
| updateAt(Int, Object)           | Update the value at the specified index with the new Object String value, throws an error if OutOfRange sn errTolerance is false
| contains(String)           | Check if the konfiger contains a key 
| enableCache(Boolean)           | Enable or disable caching, caching speeds up data search but can take up space in memory (very small though)
| errorTolerance(Boolean)           | Enable or disable the error tolerancy property of the konfiger
| isErrorTolerant() | Check if the konfiger object errTolerance is set to true
| toString()           | All the kofiger datas are parsed into valid string with regards to the delimeter and seprator

## TODOS

 - [x] create website for each implementation
 - [x] write several example in the documentation 
 - [x] examples to load and save locally in each languages
 - [x] implements size() method in all the languages
 - [x] implements clear() method in all the languages
 - [x] implemets isEmpty() method in all the languages
 - [x] enable cacheing in the konfiger
 - [x] When commiting other language must include name in the LICENCE as `Copyright (c) {Year} {Name}:konfiger` confirm
 - [x] When commiting other language author should include paypal or patreon link
 - [ ] write a desktop app to manage a key value file using fltk and c++ implementation with  command line support to test the key value feature in CLI

## How it works

Konfiger stream progressively load the key value entry from a file or string when needed, it uses two method `hasNext` which check if there is still an entry in the stream and `next` for the current key value entry in the stream. 
 
In Konfiger the key value pair is stored in a `map`, all search updating and removal is done on the `konfigerObjects` in the class. The string sent as first parameter if parsed into valid key value using the separator and delimiter fields and if loaded from file it content is parsed into valid key value pair. The `toString` method also parse the `keyValueObjects` content into a valid string with regards to the 
separator and delimeter. The value is properly escaped and unescaped.

The `save` function write the current `Konfiger` to the file, if the file does not exist it is created if it can. Everything is written in memory and is disposed on app exit hence it important to call the `save` function when nessasary.

## Contributing

Before you begin contribution please read the contribution guide at [CONTRIBUTING GUIDE](https://github.com/konfiger/konfiger.github.io/CONTRIBUTING.MD)

You can open issue or file a request that only address problems in this implementation on this repo, if the issue address the concepts of the package then create an issue or rfc [here](https://github.com/konfiger/konfiger.github.io/)

## Support

You can support some of this community as they make big impact in the traing of individual to get started with software engineering and open source contribution.

- [https://www.patreon.com/devcareer](https://www.patreon.com/devcareer)

## License

MIT License Copyright (c) 2020 [Adewale Azeez](https://twitter.com/iamthecarisma) - konfiger

