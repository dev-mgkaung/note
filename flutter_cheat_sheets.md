## Flutter Help
```python
flutter help
```
## flutter clean
## flutter doctor

## DevTools 
Precompile error solve this command
```python
flutter pub cache repair

```

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

## Build Detail Information

```python
flutter build apk -h

This command can build debug and release versions of your application. 'debug' builds support debugging and a quick development cycle. 'release' builds don't support debugging and are
suitable for deploying to app stores.

Usage: flutter build apk [arguments]
-h, --help                                        Print this usage information.
    --[no-]tree-shake-icons                       Tree shake icon fonts so that only glyphs used by the application remain.
-t, --target=<path>                               The main entry-point file of the application, as run on the device.
                                                  If the --target option is omitted, but a file name is provided on the command line, then that is used instead.
                                                  (defaults to "lib\main.dart")
    --debug                                       Build a debug version of your app.
    --profile                                     Build a version of your app specialized for performance profiling.
    --release                                     Build a release version of your app (default mode).
    --flavor                                      Build a custom app flavor as defined by platform-specific build setup.
                                                  Supports the use of product flavors in Android Gradle scripts, and the use of custom Xcode schemes.
    --[no-]pub                                    Whether to run "flutter pub get" before executing this command.
                                                  (defaults to on)
    --build-number                                An identifier used as an internal version number.
                                                  Each build must have a unique identifier to differentiate it from previous builds.
                                                  It is used to determine whether one build is more recent than another, with higher numbers indicating more recent build.
                                                  On Android it is used as 'versionCode'.
                                                  On Xcode builds it is used as 'CFBundleVersion'
    --build-name=<x.y.z>                          A "x.y.z" string used as the version number shown to users.
                                                  For each new version of your app, you will provide a version number to differentiate it from previous versions.
                                                  On Android it is used as 'versionName'.
                                                  On Xcode builds it is used as 'CFBundleShortVersionString'
    --[no-]shrink                                 Whether to enable code shrinking on release mode. When enabling shrinking, you also benefit from obfuscation, which shortens the names
                                                  of your app’s classes and members, and optimization, which applies more aggressive strategies to further reduce the size of your app.
                                                  To learn more, see: https://developer.android.com/studio/build/shrink-code
                                                  (defaults to on)
    --split-debug-info=</project-name/v1.2.3/>    In a release build, this flag reduces application size by storing Dart program symbols in a separate file on the host rather than in
                                                  the application. The value of the flag should be a directory where program symbol files can be stored for later use. These symbol
                                                  files contain the information needed to symbolize Dart stack traces. For an app built with this flag, the 'flutter symbolize' command
                                                  with the right program symbol file is required to obtain a human readable stack trace.
    --[no-]obfuscate                              In a release build, this flag removes identifiers and replaces them with randomized values for the purposes of source code
                                                  obfuscation. This flag must always be combined with "--split-debug-info" option, the mapping between the values and the original
                                                  identifiers is stored in the symbol map created in the specified directory. For an app built with this flag, the 'flutter symbolize'
                                                  command with the right program symbol file is required to obtain a human readable stack trace.

                                                  Because all identifiers are renamed, methods like Object.runtimeType, Type.toString, Enum.toString, Stacktrace.toString,
                                                  Symbol.toString (for constant symbols or those generated by runtime system) will return obfuscated results. Any code or tests that
                                                  rely on exact names will break.
    --dart-define=<foo=bar>                       Additional key-value pairs that will be available as constants from the String.fromEnvironment, bool.fromEnvironment,
                                                  int.fromEnvironment, and double.fromEnvironment constructors.
                                                  Multiple defines can be passed by repeating --dart-define multiple times.
    --split-per-abi                               Whether to split the APKs per ABIs. To learn more, see:
                                                  https://developer.android.com/studio/build/configure-apk-splits#configure-abi-split
    --target-platform                             The target platform for which the app is compiled.
                                                  [android-arm (default), android-arm64 (default), android-x86, android-x64 (default)]
    --[no-]track-widget-creation                  Track widget creation locations. This enables features such as the widget inspector. This parameter is only functional in debug mode
                                                  (i.e. when compiling JIT, not AOT).
                                                  (defaults to on)

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

## Flavours

Debug  running
```python
flutter run -t lib/main_dev.dart
flutter run -t lib/main_test.dart
```
release ruuning
```python
flutter run --flavor dev 
flutter run --flavor prod
```

## product flavor for Android
 ```python
   productFlavors{
        flavorDimensions "app"
        productFlavors {
            development {
                applicationIdSuffix '.dev'
                flavorDimensions "app"
            }
            production{
                applicationIdSuffix '.prod'
                flavorDimensions "app"
            }
            qa{
                applicationIdSuffix '.qa'
                flavorDimensions "app"
            }
    }
}
 ```
