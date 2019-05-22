# Differences between Relational and traditional (flat-file based) Software Mananegement Systems

## 1. Recompilation/Rebuild

An important difference between a relational vs. flat-file based *Software Management Systems* is the way a change in the source code repository triggers the build system to recompile/rebuild (part of the) deliverable/target modules or objects.

| Change   | Relational  | Flat-file |
---------- | ----------- | --------- |
| renaming | No          | Yes       |
| commenting | No        | Yes       |
| refactoring | No       | Yes       |


### Renaming

In traditional flat-file based *Software Mananagement Systems*, renaming variables/functions is already an error-prone task, since we are dependend on the cleverness of the editor or IDE on how we can search/replace for a specific name in our software repository, and change that name to something else, without touching text with similar/same lexical tokens with different semantic of lexical meaning. Often we get mismatches, as the name might be used as part of other names or in other unrelated contexts (such as comments or as part of a literal string) which we want to avoid.

Second, even if we manage to change the name sucessfully in all instances where that change is applicable and avoiding mismatches, this change event in the source code will trigger the build system to recompile any source text in which any textual change occured.

Clearly, in a relational system, the renaming of objects is a certain match since there is only one place that change is effectively taking place, and does not trigger a recompilation/rebuild of the source code, since all objects are uniquely define by UUID and names are just handy human-readable labels for these objects, but are not used internally by the build system to identify objects.

### Commenting

Any textual change in a source-text in a traditional flat-file *Software Management System (SMS)* will trigger recompilation of that file, even if that change only involved changes in comments, and not code.

Like in the previous case of renaming objects, in a *Relational Software Management System (RSMS)* a change in comment fields does not change the source-text, and will not trigger recompilation/rebuilding the system.

### Refactoring

When relocating a definition of some variable or function from one module to another module, in traditional *SMS* this will be a textual change in both modules, and will trigger - same as the 2 previous examples - these modules to re-compile and will rebuild the system.

Also in this case a relational SMS will not trigger recompilation for re-arranging software components/objects accross modules, as in fact a 'module' in a relational SMS is not a physical thing but only a relational thing - the module itself is not a physical object but a virtual object, or more specific it is just a container (an ordered set of objects, ordered by rank), and the placement of objects within a module is in fact quite arbitrary.

In a traditional flat-file SMS the binding between an object and a module is always static - just because we are enforced to place the source-text of that object physically in some file/module - which makes a physical connection between the object (the source-text of the object is placed at some position in that file) and the file/module.

The binding between a software component/object in a *Relational SMS* and a module (which in *RSMS* is also an object, a virtual object) is not physical but relational. The object is so-to-speak free to move to any module, as long as it is part of the repo it belongs to and can be found.

For obvious reasons (primarily for compatibility and inter-operatibility with existing *SMS*'s) in many cases we want to statically bind the object to some specific module, but as far as the RSMS is concerned, this placement is totally arbitrary and does not have to be a static binding.  We could imagine that the placement of an object in a module is not a static binding but a dynamic one, and the grouping of objects over modules be decided dynamically based on the relations between objects.

For example, if we have objects **a**, **b** and **c** and **d** and **e**, and **b** and **c** depend on **a** and **e** depends on **d**, with no further dependency, it would make sense to place **a**, **b** and **c** in one module and **d** and **e** in another module.

This feature of a *RSMS* makes it possible to implement clever algorythms to decide the grouping of objects over modules and even to have simultaneously multiple groupings of objects over modules, defined as different views over the same code repository, without the need of physical duplication of the source-code repository.

There can be use-cases in which such a feature of dynamic and multiple groupings of objects over modules would be a handy feature, for example in distributing the repository to different target systems with different (hardware/software) architecure in which a different grouping of objects over modules would be a necessary feature.




