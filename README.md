![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![version](https://img.shields.io/github/v/tag/baudee/pre-commit-serverpod)

# Serverpod pre-commit hook
A [pre-commit](http://pre-commit.com/) hook to follow the dart style guide.

Add the following in your `.pre-commit-config.yaml`. You must add the project name of your Serverpod project (it will allow the script to move to the correct directories, `projectname_flutter` and `projectname_server`):

```
- repo: https://github.com/baudee/pre-commit-serverpod
  rev: v1.0.0
  hooks:
    - id: pre-commit-serverpod
      args: ['--project-name=myproject']
```

You can also include or exclude files, by default it will only check files with the `.dart` extension, and exclude the `generated` folders:

```
- repo: https://github.com/baudee/pre-commit-serverpod
  rev: v1.0.0
  hooks:
    - id: pre-commit-serverpod
      files: lib/* 
      exclude: specific_file.dart
      args: ['--project-name=myproject']
```

Finally, you can add some arguments to the pre-commit hook:
```
- repo: https://github.com/baudee/pre-commit-serverpod
  rev: v1.0.0
  hooks:
    - id: pre-commit-serverpod
      args: ['--project-name=myproject', '--line-length=120', '--actions=analyze,format']
```

List of the arguments:

| Argument | Description                                              | Default value              |
|----------|----------------------------------------------------------|----------------------------|
| `--line-length`  | The line length that the formatter will use              | `80`                       |
| `--project-name` | The name of your Serverpod project                       | Any, this argument is mandatory |
| `--actions`      | The actions to run, can be `analyze`, `format` or `test` | `analyze,format,test`      |

Actions:
 * format: runs `dart format` on the files, and adds them to the commit
 * analyze: runs `dart analyze`, fails the commit if there are any warnigns or errors
 * test: runs `dart test`, fails the commit if there are any failing tests

