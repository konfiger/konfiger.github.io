
# <p style="text-align: center;" align="center">konfiger</p>

<p style="text-align: center;" align="center">The parent repository for this organisation, 
Contains list of implemented functions. </p>

This project is the closest thing to Android [Shared Preference](https://developer.android.com/reference/android/content/SharedPreferences) in other languages and off the Android platform.

## Table of content
- [Implemented Functions](#implemented-functions)
   - [Public Fields](#public-fields)
   - [Putting](#putting)
   - [Getting](#getting)
   - [Removing](#removing)
   - [Listeners](#listeners)
   - [Others](#others)
- [TODOS](#todos)
- [How it works](#how-it-works)
- [Contributing](#contributing)
- [Support](#support)
- [License](#license)

## Implemented Functions

The Key must always be string, the Value can be any type but the String 
value will be saved and when requested the value returned by default is the 
String value else requested with a typed get e.g. `getBoolean` then the 
value will be converted to a valid `boolean` in the language.  

### Public Fields

| Function        | Description         
| --------------- | ------------- 
| MAX_CAPACITY           | The number of datas the konfiger can take, Usually the MAX Value of `Int` in the implemented language


### Putting

The `put` functions also update the value at the location if it already in the konfiger

| Function        | Description         
| --------------- | ------------- 
| puts(String, Objects...)           | Put a Multiple Objects `Objects...` into the konfiger, each of the object string value is put
| put(String, Object)           | Put any object into the konfiger the Object value string value will be saved
| putString(String, String)           | Put a String into the konfiger
| putBoolean(String, Boolean)           | Put a Boolean` into the konfiger
| putLong(String, Long)           | Put a Long into the konfiger
| putInt(String, int)           | Put a Int into the konfiger
| putFloat(String, Float)           | Put a Float into the konfiger

### Getting

| Function        | Description         
| --------------- | ------------- 
| getAll()           | Get all the entries in the konfiger in a `Map<K, V>`


### Removing

| Function        | Description         
| --------------- | ------------- 
| remove(int)           | Remove the `KonfigerObject` at a particular index
| remove(String)           | Remove the `KonfigerObject` using the data Key 


### Listeners

| Function        | Description         
| --------------- | ------------- 
| registerListener(KonfigerListener)           | Register a new listener that get call when a change to the konfiger datas occur. 
| unRegisterListener(KonfigerListener)           | Remove a previously added listener from the konfiger

### Others

| Function        | Description         
| --------------- | ------------- 
| size()           | Get the total size of datas in the konfiger
| clear()           | clear all the datas in the konfiger. if the konfiger is attached to a file, the file is updated immediatly 
| isEmpty()           | Check if the konfiger does not have an data
| updateAt(Int, Object)           | Update the value at the specified index with the new Object String value, throws an error if OutOfRange sn errTolerance is false
| contains(String)           | Check if the konfiger contains a key 
| enableCache(Boolean)           | Enable or disable caching, caching speeds up data search but can take up space in memory (very small though)
| errorTolerance(Boolean)           | Enable or disable the error tolerancy property of the konfiger


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

The `open` function reloads the file from disk to update the `Konfiger` if changes is written to the file in another program, if the file does not exist `FileNotSpecified` exception is thrown if `errTolerance` is set to false. The `save` function write the current `Konfiger` to the file, if the file does not exist is is created if it can. If no file is specified on init everything is written in memory and is disposed on app exit.

## Contributing

Before you begin contribution please read the contribution guide at [CONTRIBUTING GUIDE](https://github.com/konfiger/konfiger.github.io/CONTRIBUTING.MD)

You can open issue or file a request that only address problems in this implementation on this repo, if the issue address the concepts of the package then create an issue or rfc [here](https://github.com/konfiger/konfiger.github.io/)

## Support

You can support some of this community as they make big impact in the developement of people to get started with software engineering.

- https://www.patreon.com/devcareer

## License

MIT License Copyright (c) 2019 Adewale Azeez - konfiger



