## Obfucating Dart Code

Flutter’s code obfuscation, when supported, works only on a release build.
1. Remove unused resources
2. Minimize resource imported from libraries
3. Compress PNG and JPEG files

```python

flutter build apk --obfuscate --split-debug-info=/<project-name>/<directory>

sample code
flutter build apk --obfuscate --split-debug-info=/apprelease_testing_demo/build/app/outputs/symbols

````


## Check Flutter Version
 
 ```python
 flutter --version 
```

## Bundle Release

```python
flutter build appbundle
```

## Apk IOS Release

```python
flutter build apk
flutter build ios
```

## Breaking down the size

```python
flutter build apk --analyze-size
flutter build appbundle --analyze-size
flutter build ios --analyze-size
flutter build linux --analyze-size
flutter build macos --analyze-size
flutter build windows --analyze-size
```
