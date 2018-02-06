# Visual Studio Code: Tips'n'Tricks and other stuff

## How to format C code

Use clang, supported by the great Microsoft VS Code extension C/C++. Build your Clang configuration file, named .clang-format, according to this short description: http://clang.llvm.org/docs/ClangFormatStyleOptions.html.

A little bit strange is the required file format of .clang-format.
All options needs to be in a single line (no line break).
Anyhow, Clang works really nice. Here is my current used configuration:

      { AlignAfterOpenBracket: true, AlignConsecutiveAssignments: true, AlignConsecutiveDeclarations: true, AlignEscapedNewlinesLeft: true, AlignOperands: true, AlignTrailingComments: true, AllowAllParametersOfDeclarationOnNextLine: true, AllowShortIfStatementsOnASingleLine: false, BreakBeforeBinaryOperators: All, BreakBeforeBraces: Allman, ColumnLimit: 0, IndentCaseLabels: true, IndentWidth: 4, UseTab: Never, ReflowComments: true }

## Like to write extensions?

VS Code's API is documented here https://code.visualstudio.com/docs/extensionAPI/overview.
Good luck!

