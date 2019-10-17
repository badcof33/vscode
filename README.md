# Visual Studio Code: Tips'n'Tricks and other stuff

## How to format C code

Use clang, supported by the great Microsoft VS Code extension C/C++. Build your Clang configuration file, named .clang-format, according to this short description: http://clang.llvm.org/docs/ClangFormatStyleOptions.html.

A little bit strange is the required file format of .clang-format.
All options needs to be in a single line (no line break).
Anyhow, Clang works really nice. Here is my current used configuration:

    AlignAfterOpenBracket: true
    AlignConsecutiveAssignments: true
    AlignConsecutiveDeclarations: true
    AlignEscapedNewlinesLeft: true
    AlignOperands: true
    AlignTrailingComments: true
    AllowAllParametersOfDeclarationOnNextLine: true
    AllowShortIfStatementsOnASingleLine: false
    BreakBeforeBinaryOperators: All
    BreakBeforeBraces: Allman
    ColumnLimit: 0
    IndentCaseLabels: true
    IndentWidth: 4
    UseTab: Never
    ReflowComments: false
    SortIncludes: false

## Extensions

- [Rewrap](https://marketplace.visualstudio.com/items?itemName=stkb.rewrap) -- Re-wraps comments and other text to a given line length.
- [Clipboard History](https://marketplace.visualstudio.com/items?itemName=Anjali.clipboard-history) -- Keep a history of your copied items and re-paste if needed


## Configure tasks

Here is my `.vscode/tasks.json` file, ready for my daily work/project:
[See](https://go.microsoft.com/fwlink/?LinkId=733558)for the documentation about
the tasks.json format

```
{
    // 
    // Requires a small wrap-script build.cmd to get this running:
    //
    // @echo"%*"
    // @pushd..\Build
    // @gbuild%*
    // @popd
    //
    "version": "2.0.0",
    "tasks": [
        {
            "label": "build DEBUG",
            "type": "shell",
            "command": "build.cmd",
            "options": {
                "cwd": "${workspaceRoot}\\C_Application\\Build"
            },
            "args": [
                "Debug.gpj"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": {
                "owner": "C",
                "fileLocation": [
                    "relative",
                    "${workspaceRoot}\\C_Application\\Build"
                ],
                "pattern": {
                    "regexp": "^\"(.*)\",\\s+line\\s+(\\d+):\\s+(warning|error|fatal)\\s+(.*)$",
                    "file": 1,
                    "line": 2,
                    "severity": 3,
                    "message": 4
                }
            }
        },
        {
            "label": "build RELEASE",
            "type": "shell",
            "command": "build.cmd",
            "options": {
                "cwd": "${workspaceRoot}\\C_Application\\Build"
            },
            "args": [
                "Release.gpj"
            ],
            "group": "build",
            "presentation": {"echo": true},
            "problemMatcher": {
                "owner": "C",
                "fileLocation": [
                    "relative",
                    "${workspaceRoot}\\C_Application\\Build"
                ],
                "pattern": {
                    "regexp": "^\"(.*)\",\\s+line\\s+(\\d+):\\s+(warning|error|fatal)\\s+(.*)$",
                    "file": 1,
                    "line": 2,
                    "severity": 3,
                    "message": 4
                }
            }
        },
        {
            "label": "clean DEBUG",
            "type": "shell",
            "command": "gbuild.exe",
            "options": {
                "cwd": "${workspaceRoot}\\C_Application\\Build"
            },
            "args": [
                "Debug.gpj",
                "-clean"
            ],
            "group": "build",
            "problemMatcher": []
        },
        {
            "label": "clean RELEASE",
            "type": "shell",
            "command": "gbuild.exe",
            "options": {
                "cwd": "${workspaceRoot}\\C_Application\\Build"
            },
            "args": [
                "Release.gpj",
                "-clean"
            ],
            "group": "build",
            "problemMatcher": []
        }
    ]
}
```

## Like to write extensions?

VS Code's API is documented here https://code.visualstudio.com/docs/extensionAPI/overview.
Good luck!
