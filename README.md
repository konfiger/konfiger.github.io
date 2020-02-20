
# <p style="text-align: center;" align="center">konfiger</p>

<p style="text-align: center;" align="center">The parent repository for this organisation, 
Contains list of implemented functions. </p>

This project is the closest thing to Android [Shared Preference](https://developer.android.com/reference/android/content/SharedPreferences) in other languages and off the Android platform.

## Table of content
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
| KonfigerStream(String)           | Set the KonfigerStream file path, this cannot be changed, the default delimeter(`=`) and seperator(`\n`) will be used
| KonfigerStream(String, Char, Char)   | Set the KonfigerStream file path, this cannot be changed, the second param is the delimeter and the third param is the seperator

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
| MAX_CAPACITY           | The number of datas the konfiger can take, Usually the MAX Value of `Int` in the implemented language


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
| read(String)          | Dispose all the current data and read new datas from the file path, the konfiger IO path is changed to the file path sent as parameter
| append(String)          | Read new datas from the file path and append the datas into the current konfiger, the konfiger IO path is not changes
| reload()         | Reload changes from the konfiger IO path
| save()         | Save the konfiger datas into it IO path if specified, if no IO path specifed the datas remain in memory, this does not clear the data

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
| toString()           | All the kofiger datas are parsed into valid string with regards to the delimeter and seprator
| toJSON()           | All the kofiger datas are parsed into valid JSON string without regards to the delimeter and seprator
| caseSensitive(Boolean)           | Change the key case sensitivity, it is effective from the point of changing

## TODOS

 - [x] create website for each implementation
 - [ ] write several example in the documentation 
 - [ ] examples to load and save locally in each languages
 - [x] implements size() method in all the languages
 - [x] implements clear() method in all the languages
 - [x] implemets isEmpty() method in all the languages
 - [x] enable cacheing in the konfiger
 - [ ] When commiting other language must include name in the LICENCE as `Copyright (c) {Year} {Name}:konfiger` confirm
 - [ ] When commiting other language author should include paypal or patreon link

## How it works

KonfigerObject class contains the key and value field and the fields setter and getter. The KonfigerObject is the main internal type used in the Konfiger class.
 
In Konfiger the key value pair is stored in `Array[]` type, all search updating and removal is done on the `konfigerObjects` in the class. The string sent as first parameter if parsed into valid key value using the separator and delimiter fields. The `toString` method also parse the `keyValueObjects` content into a valid string with regards to the 
separator and delimeter. The value is properly escaped and unescaped.

The `reload` function reloads the file from disk to update the `Konfiger` if changes is written to the file in another program, if the file does not exist `FileNotSpecified` exception is thrown if `errTolerance` is set to false. The `save` function write the current `Konfiger` to the file, if the file does not exist is is created if it can. If no file is specified on init everything is written in memory and is disposed on app exit.

## Contributing

Before you begin contribution please read the contribution guide at [CONTRIBUTING GUIDE](https://github.com/konfiger/konfiger.github.io/CONTRIBUTING.MD)

You can open issue or file a request that only address problems in this implementation on this repo, if the issue address the concepts of the package then create an issue or rfc [here](https://github.com/konfiger/konfiger.github.io/)

## Support

You can support some of this community as they make big impact in the developement of people to get started with software engineering.

- https://www.patreon.com/devcareer

## License

MIT License Copyright (c) 2020 Adewale Azeez - konfiger



