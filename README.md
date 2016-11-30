# Visual Studio Code: Tips'n'Tricks and other stuff

## How to format C code

Use clang, supported by the great Microsoft VS Code extension C/C++. Build your Clang configuration file, named .clang-format, according to this short description: http://clang.llvm.org/docs/ClangFormatStyleOptions.html. 

A little bit strange is the required file format of .clang-format. 
All options needs to be in a single line (no line break). 
Anyhow, Clang works really nice. Here is my current used configuration:

      {BasedOnStyle: LLVM, IndentWidth: 4, UseTab: false, BreakBeforeBraces: Allman, AllowShortIfStatementsOnASingleLine: false, AlignAfterOpenBracket: true, AlignConsecutiveAssignments: true, IndentCaseLabels: true, ColumnLimit: 80, ReflowComments: true, AlignTrailingComments: true, BreakBeforeBinaryOperators: All}
