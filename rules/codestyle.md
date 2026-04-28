# Codestyle
- The code has to be as minimalistic as possible. If there is standard-functionality, use well known libraries to make the code as simple as possible.  
- Use any programming-language/framework/library that makes the code simplest and most readable
- if a single class is not the only thing a file contains, constants that are longer than three lines should be extracted from the class
- if a file contains multiple classes and one depends on another, the dependend class must come first because it is more important
- if there are exclusive dependencies between files or folders, they must be wrapped inside a folder, if the dependency is unidirectional the folder must get the name of the dependant file
- a function can never be longer than 15 lines except it is a pure mapping-function, otherwise it must be extracted
- dont just group loose function into files if they only have one dependant caller
- don't make micro-extractions, if a function is shorter than 5 lines and the extracted function that is exclusively referenced from this function to, undo the extraction

## Pure mapping-function
This is a function that does only map date and nothing else. It is not allowed to consist of a loop for example.  

## Dependency-levels in files
The following dependency-rules apply to all of these units and every combination of them:  
- constant-definitions and  that are longer than three lines
- functions
- class definitions

If a file contains a unit that directly depends on more than one subunit, then no subunit of those subunits may remain in the same file.
In that case, the file may only contain:
 - the parent unit
 - its direct subunits
Any deeper dependency level must be moved into a separate dependant-named file or folder.
A same-file dependency chain is only allowed when each unit has exactly one exclusive dependant in that file, so the file reads strictly top-down as a single chain.