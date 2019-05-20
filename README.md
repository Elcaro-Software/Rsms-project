# ELCARO project

OPM is part of Elcaro Project. Further reading: (will be supplied later).

## OPM - Object Process Model

Tags: *Source control*, *Make/Build*, *Version system*, *Editor*, *IDE*

Key feature: Applying the features of database renormalization to programming / source code.

Note: Shares similararity with the concept of Intentional Programming (IP), storing source text in grammatical form (abstract syntax tree or AST). 

See: [intentional programming] (https://en.wikipedia.org/wiki/Intentional_programming)

### Summary

Store 'objects' in memory/database instead of a file system, including
- Object dependency
- Object version

Objects are either **real objects** or **virtual objects**.

A **real object** is a *data object* or *process object*. 

A **virtual** object is for example a group of objects.

For instance a module group which is an ordered set of objects. Objects are ordered by *rank* where each object in a lower rank does not depend on objects in the same group of a higher rank. 

For example the sample code:

    int x = 1;
    int y = 2;
    int z = x + y;

Would place this code sample in the following ranking order:

    (rank 0):	int x = 1;
    (rank 0):	int y = 2;
    (rank 1):	int z = x + y;

A code view might display the elements of the code sample elements with the same rank in any order. 

For example the following is a valid view of this code example:

    int y = 2;
    int x = 1;
    int z = x + y;

A **real object** contains source code and (compiled) object code (bytecode).

Compiling an object is recursive compilation of all invalid objects the object depends on, and the object itself.


### Design goals

1. **Maintainance**

A primary design goal for OPM is to ease maintaining large software repositories. The way in which OPM can achieve that is based on a few features op OPM.

* *Relational model*

Firstly, the sources are stored in their grammatical form in a renormalized form. Both a versioning system and a build system will benefit greatly from that design. Many tasks of code develoment become significanty easier and less error-prone. Errors in the code which would normally only show up after compilation (or at runtime) can already be catched during the edit session when storing the changes.

* *Integrated versioning system*

Placing code in a versioning system does not rely on external tools, but is an integral part of the OPM IDE.

* *Integrated build system*

Also the build system is integral part of the OPM IDE, and does not rely on external build tools. 

2. **Internationalization**

When working with international teams with different national languages and different coding styles, OPM facilitates to enter and view the code using individual preferences so that naming of variables and even language keywords and code formatting can be adjusted to personal preference. This also extends to code documentation (code comments and external documentation). 

3. **Integration with external tools**

Although OPM itself does not rely on any external tool for building or maintaining software, it will often be needed to use repositories build with tradional (flat file) code repositories and build tools and versioning systems or to develop code that gets exported to traditional maintainence tools. 

OPM can interact with such repositories by providing tools for:

* **External import**

External code repositories can be imported into OPM from flat file or most common versioning systems (GIT, SVN, ...) and the type of build system can be semi-automatically detected and translated to OPM.
Those parts of the build system that can not be automatically detected and translated into OPM gets reported when trying to import an external repository, and the missing information can be supplied by providing an OPM configuration import file.

* **External export**

OPM code repositories can be exported from OPM into a flat file repository or versioning system (...) and an external build system (configuration and make files) can be semi-automatically generated for most common build systems. For (possible) future (re)imports an OPM import file is supplied too.


### Introduction

*Relational storage system instead of flat files*

Most programming languages and environments and development tools operate on source text as *flat files*.

In traditional (flat file) based development systems recompilation of source code occurs for every change in the source text. Even when no source code is affected. And if only a few code objects are changed, all other objects contained in the file are recompiled too.

For small size projects, the difference is not noticable, due to the compilation speed of most compilers in use today. But for large or ultra-large projects, the difference may become noticable.

Also for other operations like including header files or linking to external libraries, require that these objects (compiled or source) are treated as files, not objects.

If we treat objects as seperate things, with each object having its own dependency list, and also include the versioning of objects (different versions of the same object can have different dependency lists) this eliminates the need for external tools for keeping versions (like git, svn) and make/build tools for which we have to give explicit information about the dependency of targets (expressed as make rules).

In the OPM model such dependencies are *generically intrinsic* and built into the OPM IDE.

*Integrated versioning system*


*Integrated build system*

A target object is the result of the invocation of some version of a process (which is also an object) which uses a version of parameter set for input values (which is also an object) and a set of source files (which are also versioned objects).
 
This works recursively as both the parameter set or input set of source files can themselves be defined as targets.

Editing a source object will also compile the object and make a new version of the object. 

If the compilation is unsuccesfull, there is no compiled code but instead an error indicator and message and position of the error in the source text and a flag is set that the object is invalid. All objects dependent on that object will then become invalid too. 

If the compilation is succesfull, all objects dependend on this object will be recompiled too. In many cases this is a no-op, but in some case objects which were invalid can become valid due to the fact the object which that object depends on was recompiled and became valid.

The editor behaviour of automatic recompilation of dependend objects is adjustable and can be set to be postponed untill the end of the edit session, to avoid unnecessary multiple recompilation of the same object. For interactive sessions though automatic recompilation is a handy feature to check for errors as soon as possible. 

*Identifying objects*

Objects are not identified by name but by UUID. Names of objects are just labels. So objects can have same names but different UUID.
In the editor such ambiguous names are resolved by qualifying the names with the namespace the object belongs to and requiring that within
each namespace the name of objects are unique.

Renaming objects then becomes a trivial task since renaming an object only replaces the unique instance of a label of that object, and avoids errors that can result from tools that do textual search/replace.

One disadvantage would be that while textual search/replace can also (correctly) rename text in comments, the OPM editor would not touch comments. One way of accomodating for that wanted behaviour is to allow within comments such tagged fields which automatically display text such as objectnames correctly as they refer to the object UUID.

(to be finished later)
