---
Title: Recap CMake practical guide
Description: 
Date: 15-02-2021
Tags:
References: [[Professional_CMake_A_Practical_Guide.pdf]]
Editor: markdown
---

# Professional CMake a practical guide

## General knowledge
Command names are case insensitive, so the following are all equivalent:
```c++
add_executable(...)
ADD_EXECUTABLE(...)
Add_Executable(...)
```

## Chapter 3

#### Required to setup basic c++ project
3 basic commands that are required in every CMakeList.txt file: 
- **cmake_minimum_required**(*version*)
CMake is continually updated and extended to add support for new tools, platforms and features. This should always be the first line of the CMakeList file. 

- **project**(*projectName*)
The command does much more than just populate a few variables. Every CMake project should contain a project() command and it should appear after cmake_minimum_required() has been called. It contains the name of the project.

- **add_executable**(*targetName source1*)
Tells CMake to create an executable from a set of source files.

##### example:
```c++
// example
cmake_minimum_required(VERSION 3.2)
project(MyApp)
add_executable(myExe main.cpp)
```

##### Recommended practices
If creating a project intended to be built and distributed as part of the operating system itself (common for Linux), the minimum CMake version is likely to be dictated by the version of CMake provided by that same distribution.

## Chapter 4: Building simple Targets
Read chapter 4.1 if you want to make executables other than console applications. E.g. apple platforms or windows GUI applications.

### Creating libraries
For many larger projects the abilitiy to create and work with libraries is also essential to keep the project manageable. 

Creating libraries has an analogous form compared to *add_executable*

``` # Creating library
add_library(targetName [STATIC | SHARED | MODULE]
						[EXCLUDE_FROM_ALL]
						source1 [source2 ...]
)
```


targetName is used within the CMakeLists.txt file to refer to the library. The name of the built library on the file system being derived from this name by default. 

#####  Recommended practices

- target names need *NOT* be related to the project name. It is common to see tutorials and examples use a variable for the project name and reuse that variable for the name of an executable target like so:
 ``` # Poor practice, but very common
set(projectName MyExample)
project(${projectName})
add_executable(${projectName} ...)
```

- When naming targets for libraries, resist the temptation to start or end the name with lib. On many platofrms (i.e. just about all execpt Windows), a leading *lib* will be prefixed automatically when constructing the actual library name. Which could result in *liblibsomething*.

- Aim to always specify PRIVATE, PUBLIC and/or INTERFACE keywords when calling the target_link_libraries() command. (see course 4.3)

## Chapter 5: Variables (types)
#### Normal variables
In CMake, a variable has a particular scope, much like how variables in other languages have a scope limited to a particular function, file, etc. A variable cannot be read or modified outside of its scope. 

```
	set(varName value... [PARENT_SCOPE])
	unset(myVar) # remove variable
```

#### Environment Variables
CMAke also allows the value of environment variables to be retrived and set using a modified form of the normal variable notation. The value of an environment variable is obtained using the special form $ENV{varName} and this can be used anywhere a regular ${varName} form can be used. Setting an environment variable can be done in the same way as an ordinary variable, except with ENV{varName} instead of just varName as the variable to set. For example:

```
set(ENV{PATH} "$ENV{PATH}:/opt/myDIR")
```

#### Cache variable (section 5.3)
Unlike normal variables which have a lifetime limited to the processing of the CMAKELists.txt file, cache variables are stored in the special file called CMakeCache.txt in the build directory and they persist between CMAKE runs. Once set, cache variables remain set until something explicitly removes  them from teh cache. The value of a cache variable is retrieved in exactly the same way as a normal variable. But the set() command is different when used to set a cache variable. 

```
set(varName value... CACHE type "docstring" [FORCE])
```

**FOR MORE DETAILS ABOUT SETTING CACHE VARIABLE OPTIONS CHAPTER 5.3)**

##### Boolean Cache variable
Setting a boolean cache is very common => seperate comamnd expressly for that purpose. If *initialValue* is not present, the default value OFF will be used. 

```
option(optVar helpString [initialValue])
```

#### Debuggin variables and diagnostics
Print out diagnostic messages and variable values during the CMake run. The mode can be: *STATUS, WARNING, AUTHOR_WARNING, SEND_ERROR, FATAL_ERROR, DEPRECATION*
```
	message([mode] msg)
	
	#example
	
	set(myVar "Hello There")
	message("The value of myVar = ${myVar}")
```

##### advanced
The variable is watched, all attempts to read or modify it are logged. For the vast majority of cases, simply listing the variable to be watched without the optional command is sufficient. However, a command can be given which will be executed every time the variable is read or modified. The command is expected to be the name of a CMake function or macro (chapter 8)
```
variable_watch(myVar [command])
```

###### Best practices
- Try to establish a variable naming convention early. e.g. prefix with the project name. The project could grow fast resulting it the become a sub-part of some larger project. 
- For log messages inteded to remain as part of the build, aim to always specificy a mode with the message() command. If the message is of a general informational nature, prefer to use STATUS rather than no mode keyword. Don't use modes for temporary debugging messages. 
- CMake provides a larger number of pre-defined variables that provide details abou tthe system or influence certain apsects of CMake's behavior. It is therefore recommended for developers to occassionally make a quick scan through the CMake documentation page listing the pre-defined variables to help bgecome familiar with what is available. 

## Chapter 6: Flow control 
A common need for CMake projects is to apply some steps only in certain circumstances. If/else, Loops, foreach, while, interrupting loops, ...

## Chapter 7: Using subdirectories
### add_subdirectory()
The add_subdirectory() command allows a project to bring another directory into the build. **That directory must have its own CMakeLists.txt file which will be processed at the point where add_subdirectory() is called.**

```
add_subdirectory(sourceDir)
```

The add_subdirectory requires an own CMakeList.txt file. That is a new scope that acts like a child of the c alling scope and there are number of effects:

- All variables defined in the calling scope will be visible to the child scope.
- Any new variable created in the child scope will not be visible to the calling scope. 
- Any change to a variable in the child scope is local to that child scope. The calling scope's variable is left uncahnged. The variable modified in the child scope acts like a new variable that is discarded when processing leaves the child scope. 

### include()
```
include(filename)
include(module)
```

The first form is somewhat analogous to add_subdirectory(), but there are number of important differences:

- Include() expects the name of a file to read in, whereas add_subdirectory() expects a directory and will look for a CMakeLists.txt file within that directory. The file name passed to include() typically has the extension .cmake, but it can be anything. 

- Include() does not introduce a new variable scope, whereas add_subdirectory() does. 

- Both commands introduce a new policy scope by default, but the include() command can be told not to do so with the NO_POLICY_SCOPE option. 

- The value of the CMAKE_CURRENT_SOURCE_DIR and CMAKE_CURRENT_BINARY_DIr variables do not change when processing the file named by include(), whereas they do change for add_subdirectory(). This will be discussed in more detail shortly. 


###### Recommended practices
- As a general guide, most simple projects are probably better off preferring to use add_subdirectory() over include(). 
- Irrespective of whether using add_subdirectory(), include() or a combination of both, the CMAKE_CURRENT_LIST_DIR variable is generally going to be a better choice than CMAKE_CURRENT_SOURCE_DIR. 

## Chapter 8: Functions and macros

## Chapter 9: Properties

## Chapter 11: Modules

# Builds in depth
## Chapter 13: Build type
# The Bigger Pciture

## Chapter 24: Testing
## Chapter 27: External Content
### FetchContent
In projects that depend on many external projects, it can sometimes be the case that those external projects in turn share some common dependencies. It would be undesirable to download and build those common dependencies multiple times. The FetchCotnent module offers a solution to this scenario. 

example:
```
include(FetchContent)
FetchContent_Declare(googletest // 1
	GIT_REPOSITORY https://github.com/google/googletest.git
	GIT_TAG				 TAG_HERE	# release 1.8.0
)
 
FetchContent_GetProperties(googletest) // 2
if(NOT googletest_POPULATED)
	FetchCotnent_Populate(googletest)
	add_subdirectory(${googletest_SOURCE_DIR} ${googletest_BINARY_DIR}) // 3
endif()
```

1. Record details of where GoogleTest should be obtained from. 
2. Populate the GoogleTest contents, but only if some other part of the project hasn't already done so. 
3. Always provide both xxx_SOURCE_DIR and xxx_BINARY_DIOR to add_subdirectory(). Where xxx_SOURCE_DIR poitns to a location not in the current binary directory (and this is typically what occurs), add_subdirectory() requires that associated binary directory to be given as well. 


## Chapter 28: Project Organization
 #### Common TOP Level Subdirectories
 directories:
 - cmake
 - dependencies
 - doc
 - src
 - tests
 - packaging
 