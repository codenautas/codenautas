## Draft for future coding conventions and guidelines of Codenautas projects

### Porpuose
This document collects de facto coding conventions used in current projects, starting with a simple list with little or no clasification.
Hopefully, subsecuent versions of this documents will evolve into a more consistent classification.

### Node projects
* New projects should be created using [qa-control command-line utility](https://github.com/codenautas/qa-control) that generates a template with the minimal
  required setup, for example:
  
  ``` mkdir myproject && cd myprojects && qa-control --init```
* Source code editor settings:
  * File encoding: UTF8 without BOM
  * Tabs according by file-type:

      ext | width
    ------|-------
      js  |   4
      md  |   2
    jade  |   2

  * Replace tabs with spaces
* Multi-language documentation should be written in github's style of markdown, starting in LEEME.md file, providing at least a description in english and spanish.
  * [multilang](https://github.com/codenautas/multilang) should be used to generate (from LEEME.md) README.md and other language files
  * Warning: README.md is required for npmjs.com publication
* [qa-control](https://github.com/codenautas/qa-control) can be used to check for various conventions including package.json format and depenencies,
  .gitignore, jshint/eslint warnings and "cucardas"

