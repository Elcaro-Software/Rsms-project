# FUTURE

This file describes the bicycle lane and railway track into the future of this repository.

# GOALS

## 1. Prototype System

* Single user RDBMS as storage system (SQLITE)
* Support for 1 programming language, in 1 familiy, in 1 dialect and 1 flavour (GNU C - C11)
* Support for 1 architecture / OS (Ubuntu 18.04 / Linux ...)
* Support for 1 national language / character set
* Command-line interface only
* Various accompanying tools

## 2. Multi-user, Multi-platform, multi ProgLang, Multi NatLang / CharSet

* Multiple concurrent users on an RDBMS supporting it (MySQL / MariaDB / PostgreSQL)
* Support for multiple programming languages in different families, dialects and flavours
  (minimal: C, C++, Rust, Java, Python)
* Support for multiple architectures / OS's (minimal: Linux, Windows, Mac)
* Support for multiple national languages / charsets 
  (minimal: Eur. languages - FRA, GER, ENG, SPA, POR, SWE, FIN, ITA - Asian languages - CHN, KOR, JAP, THA, MAL, IND, HIN - MeNa languages - ARA, FAR)
* Graphical user-interface
* Graphical reporting
* Extended toolset

## 3. Full System

* Transactional database SERIALIZABLE
* Extended support for all major architectures / platforms / OS's
* Extended support for aditional programming languages, covering all major programming paradigms, including:

  Concatenative languages: Forth, Factor

  Functional languages: Haskell, Lisp, Scheme, J, K, APL, Erlang, F#
  
  Object-oriented: C#, Eiffel, D, Ruby
  
  Dataflow: Lucid
  
* Legacy support for older prog. lang (COBOL, FORTRAN, ALGOL60/68)
* Full national language & characterset support for all major languages and character sets. (Adding east-eur languages, like Greek, Serbian, Kroatian, Romanian, Bulgarian, Polish, Chech, Ukranian, Russian, African languages like Amhara, Swahili, Asian languages like Birmese, Tamil, Vietnamese).
* Extended (graphical) user-interface & tool-set

# STAGES

## STAGE: PREPARATION

1. Initial documentation describing the general concept & principles of RSMS and OPM and comparsion with:
* Intentional Programming (IP)
* Traditional build systems
* Traditional version systems
2. Investigation of the most important aspects of:
* Hardware / architecture / OS /platforms
* National languages and charactersets
* Programming languages
* Build systems
* Version systems
3. 

## STAGE: ANALYSIS


## STAGE: DESIGN


## STAGE: IMPLEMENTATION

### DATA MODEL

First step in the implementation is to develop a provisional data-model for OPM (the core system) and add-on systems 
(like Issue Tracking, Change Management).

It wil consist of at least:
* Hardware, architecture and operating system & environment RSMS can be used on and built on.
* The build-system
* The version-system
* Programming language support (parser/lexer)

Outcomes:
* E/R definitions & diagrams
* Table design

### PROCESS MODEL


