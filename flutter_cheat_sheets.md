## Flutter Command Option Guide
``` python
flutter -h

Available commands:
  analyze                  Analyze the project's Dart code.
  assemble                 Assemble and build flutter resources.
  attach                   Attach to a running application.
  bash-completion          Output command line shell completion setup scripts.
  build                    Flutter build commands.
  channel                  List or switch flutter channels.
  clean                    Delete the build/ and .dart_tool/ directories.
  config                   Configure Flutter settings.
  create                   Create a new Flutter project.
  devices                  List all connected devices.
  doctor                   Show information about the installed tooling.
  downgrade                Downgrade Flutter to the last active version for the current channel.
  drive                    Runs Flutter Driver tests for the current project.
  emulators                List, launch and create emulators.
  format                   Format one or more dart files.
  generate                 run code generators.
  install                  Install a Flutter app on an attached device.
  logs                     Show log output for running Flutter apps.
  make-host-app-editable   Moves host apps from generated directories to non-generated directories so that they can be edited by developers.
  precache                 Populates the Flutter tool's cache of binary artifacts.
  pub                      Commands for managing Flutter packages.
  run                      Run your Flutter app on an attached device.
  screenshot               Take a screenshot from a connected device.
  symbolize                Symbolize a stack trace from an AOT compiled flutter application.
  test                     Run Flutter unit tests for the current project.
  upgrade                  Upgrade your copy of Flutter.
  version                  List or switch flutter versions.
  
````


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
