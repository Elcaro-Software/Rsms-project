# README.md

Project: Elcaro

Subproject: OPM - Object Process Model

Status: Unfinished (no code yet). See: [History]

[History]: https://github.com/Elcaro-Software/opm/blob/master/HISTORY.md

Start date: 21 may 2019

## Short Description

*Object Process Model* (OPM) aims to be an **Integrated Development Environment** (IDE), but contrary to most other IDE's works with a storage format of the source code in a relational database (in renormalized/grammatical format) instead of a flat file system, quite similar to the concept of **Intentional Programming (See: [IP]**).

[IP]: https://en.wikipedia.org/wiki/Intentional_programming "Intentional Programming"

An advantage of this approach is that a versioning system and build system can be built quite easiliy on top of OPM and be integral part of the IDE, where most other IDE's would rely on external tools for a versioning- and build system.

Also **Issue Tracking (IT)** and **Change Management (CM)** can be built quite easy on top of OPM. A change in **CM** is the resolution for one or more issues in **IT** and an issue is resolved by one or more changes. A **User Session (US)** is applied to a repository to implement one or more changes, and a change can be implemented using one or more **US** on the repository.

## OPM

The *Object Process Model* starts out from the basic idea that a **Target Object (TO)** is the result of the invocation of (some version) of a **Process Object (PO)** (which in OPM is an Object), using some **Input Parameter Set (IPS)** (which in OPN is also considered an Object) and some **Source Object Set (SOS)** (which in OPM is also considered to be an Object). In many cases the invocation of a process that creates the target object also creates other objects, so the target object is part of a **TYarget Object Set (TOS)** (which also is an Object in OPM).

In essence, this is also the way most build/make systems work in which we define dependency rules and operations that needs to be performed to create a target depending on one or more sources, with the exception that in OPM also the Process itself and the Parameter list are objects and can be target objects which themselves are results of the invocation of other processes to recreate the target, and so on.

Second, the OPM model has a finer granularity of object dependency then traditional build tools (which work on flat files) as source text is not stored as modules, but as individual objects in its grammatical, renormalized form as an **Abstract Syntax Tree (AST)**, so the dependencies are not just defined on the level of modules (files) but on the level of objects.

## Further reading

See: [OPM]

[OPM]: https://github.com/Elcaro-Software/opm/blob/master/opm.md "OPM"
