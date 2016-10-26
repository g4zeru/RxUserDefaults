# RxUserDefaults

[![CI Status](http://img.shields.io/travis/num42/RxUserDefaults.svg?style=flat)](https://travis-ci.org/num42/RxUserDefaults)
[![Version](https://img.shields.io/cocoapods/v/RxUserDefaults.svg?style=flat)](http://cocoapods.org/pods/RxUserDefaults)
[![License](https://img.shields.io/cocoapods/l/RxUserDefaults.svg?style=flat)](http://cocoapods.org/pods/RxUserDefaults)
[![Platform](https://img.shields.io/cocoapods/p/RxUserDefaults.svg?style=flat)](http://cocoapods.org/pods/RxUserDefaults)


Overview
-------
Reactive UserDefaults, inspired by [rx-preferences].

Typehandling was inspired by [wrap] and [unbox]


## Usage

There is only one class called Setting.

To create a setting use the constructor of that class:
```swift
let setting = Setting<String>(userDefaults: userDefaults, key: "INSERT_KEY", defaultValue: "DEFAULT")
```
The arguments should be self explanatory.

Currently only following Types are supported:
- String
- Int
- Bool
- Array (only with the types supported by the UserDefaults)
- Enum (but enum must conform to the RxSettingEnum protocol)

Functions you can use:
```swift
// gets the value
let val = setting.value 

// sets the value
setting.value = val 

// check if value is saved (note: the default value is not automatically saved)
setting.isSet

// deletes the value
setting.remove()

// provides a hot observable that triggers on every change
// and starts with the current value (or default value)
setting.asObservable()

```
## Warnings & TODOs

Currently the reactive stream only fires if you change the value through the Setting class. 
I have not found a good solution (that does not require KVO) to observe changes.

I want to support everything that the UserDefaults support (e.g. Dictionary, URL ...).
For now you can expand the library to more types by conforming to the RxSettingCompatible protocol.
But note that persisting types that are not supported by the UserDefaults will fail silently.


## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

## Installation

RxUserDefaults is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "RxUserDefaults"
pod 'RxSwift', '3.0.0-beta.1'
```

## Requirements

- [RxSwift](https://github.com/ReactiveX/RxSwift)


## Author

David Kraus, kraus.david.dev@gmail.com


License
-------

    Copyright 2016 Number42

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


[rx-preferences]: https://github.com/f2prateek/rx-preferences
[wrap]: https://github.com/JohnSundell/Wrap
[unbox]: https://github.com/JohnSundell/Unbox







