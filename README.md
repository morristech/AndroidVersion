# Android Version plugin

## Usage

### Apply plugin

```groovy
buildscript {
    repositories {
        maven {
            url "https://plugins.gradle.org/m2/"
        }
    }

    dependencies {
         classpath "gradle.plugin.si.kamino.gradle:android-version:1.0.0"
    }
}

apply plugin: 'si.kamino.android-version'
```

### Configuration

```groovy
androidVersion {

    appVersion {
        versionCode {
            digits 2
        }
    }

    variants {
        variant1 {
            major 1
            minor 2
            build 6
        }

        variant2 {
            major 0
            minor 0
            build 1
        }

    }
    
    splts {
        abi {
            x86 {
                versionCode(AddVersionCode) {
                    add 1000000
                }
            }
        }
    }

}
```

#### Version code types

`SimpleVersionCode` creates version code from version name parameters (`major`, 'minor' and 'build'). By default 
each part will take up 2 digits but this is configurable through `digits` parameter.

`StaticVersionCode` sets static value defined in `versionCode` parameter.

`AddVersionCode` sums previously calculated value and value defined in `add` parameter.

By default plugin will set `SimpleVersionCode` with digits set to 2.

## Limitations 

There are some instant run limitations at the moment due to [bug](https://code.google.com/p/android/issues/detail?id=227610) in Android Studio.
Due to this issue plugin will be disabled if it detects that it is running under instant run. That means that version name will be empty 
and version code will be 0. That is ok for tho most cases, if not you can still set version the old way in `android.defaultConfig`.
When not using instant run that value will be overridden by this plugin.

## License 

    MIT License
    
    Copyright (c) 2017 Kamino d.o.o.
    
    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:
    
    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.
    
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
