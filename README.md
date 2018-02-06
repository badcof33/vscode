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

## A custom task file

The file `tasks.json` shall be located in the `.vscode` in your projects root directory. It controls which project build commands are supported and how to run them. See https://go.microsoft.com/fwlink/?LinkId=733558 for the documentation about the `tasks.json` format.

### Redirect STDERR to STDOUT

Some tools output the error messages to STDERR instead of STDOUT. So you have to redirect the tool output to STDOUT so that Code can parse this with task parameter "pattern". Set parameter "command" in tasks.json` to call 'build.cmd' to achieve the job. On Windows, it looks like this:
    
      @echo"%*"
      @pushd..\Build
      @gbuild %* 2>&1
      @popd
          
