# doconce2
Features and goals targeting the next major version of DocOnce

## Implementation
* Full refactoring of the code
  * Should make use of packages and directories
* Full compatibility with the most recent versions of Python 3. Should also try to maintain support for Python 2.6 and 2.7.
* Fix encoding issues
  * Unicode everywhere internally
  * UTF-8 as default encoding for files
* Minimize use of temporary files
  * Excessive use of temporary files impose restrictions on parallel executions of DocOnce
* Full multi-step parsing
  * Should make testing much easier
* Asynchronous I/O (including processing of OSCMD, images, etc.)


## Features

### Mandatory
* Full pgfplots/TikZ support
* Environments for example, theorem, proof, etc. to attract LaTeX users

### Nice-to-have
* A command similar to `latexmk` for DocOnce
