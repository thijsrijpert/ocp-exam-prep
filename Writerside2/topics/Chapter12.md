# Chapter 12 (Modules)

## javac

| Option        | Description                                                                            |
|---------------|----------------------------------------------------------------------------------------|
| -cp           | Class Path (classes that are required to be known, has access to module path)          |
| --class-path  | Class Path (classes that are required to be known, has access to module path)          |
| -classpath    | Class Path (classes that are required to be known, has access to module path)          |
| -d            | Directory (place to dump the generated files)                                          |
| -p            | Module Path (path to place modular jars / classes, does not have access to classpath)  |
| --module-path | Module Path (path to place modular jars / classes, does not have access to classpath)  |

## java

| Option                   | Description                                                                                      |
|--------------------------|--------------------------------------------------------------------------------------------------|
| -cp                      | Class Path (classes that are required to be known, has access to module path)                    |
| --class-path             | Class Path (classes that are required to be known, has access to module path)                    |
| -classpath               | Class Path (classes that are required to be known, has access to module path)                    |
| -d                       | Describes the module, indicates the packages in the module, the exports and the required modules |
| --describe-module        | Describes the module, indicates the packages in the module, the exports and the required modules |
| -p                       | Module Path (path to place modular jars / classes, does not have access to classpath)            |
| --module-path            | Module Path (path to place modular jars / classes, does not have access to classpath)            |
| --list-modules           | Lists observable modules without running program                                                 |
| --show-module-resolution | Shows modules when running program                                                               |

## jar

| Option            | Description                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
| -c                | Creates a new jar file                                                                           |
| --create          | Creates a new jar file                                                                           |
| -v                | Prints details when creating the jar file                                                        |
| --verbose         | Prints details when creating the jar file                                                        |
| -f                | JAR filename                                                                                     |
| --file            | JAR filename                                                                                     |
| -C                | Set the working directory                                                                        |
| -d                | Describes the module, indicates the packages in the module, the exports and the required modules |
| --describe-module | Describes the module, indicates the packages in the module, the exports and the required modules |

## jdeps

jdeps creates a list of packages (and thus modules) the application depends on

| Option          | Description                                                                               |
|-----------------|-------------------------------------------------------------------------------------------|
| --module-path   | Module Path (path to place modular jars / classes, does not have access to classpath)     |
| -s              | Summarizes output, only output module dependencies (don't include the packages)           |
| -summary        | Summarizes output, only output module dependencies (don't include the packages)           |
| --jdk-internals | Outputs any dependencies on internal jdk apis, and a guide on how to mitigate this issue  |
| -jdkinternals   | Outputs any dependencies on internal jdk apis, and a guide on how to mitigate this issue  |

## jlink
| Option        | Description                                                                             |
|---------------|-----------------------------------------------------------------------------------------|
| --module-path | Module Path (path to place modular jars / classes, does not have access to classpath)   |
| --add-modules | The modules to include in this jar (also includes the dependencies of supplied modules) |
| --output      | Output directory                                                                        |
