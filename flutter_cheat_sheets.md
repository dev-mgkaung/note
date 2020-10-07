## Obfucating Dart Code

Flutter’s code obfuscation, when supported, works only on a release build.


```python

flutter build apk --obfuscate --split-debug-info=/<project-name>/<directory>

sample code
flutter build apk --obfuscate --split-debug-info=/apprelease_testing_demo/build/app/outputs/symbols

````
