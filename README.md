# file-reader-ation

> GitHub Action to read the contents of a file

This is a GitHub Action to read the contents of a file. Give it a path to a file and it provides you with the file's contents, accessible through an output variable.

## Usage

The following example [workflow step](https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow) will read the contents of the `package.json` file.

```yml
- name: "Read file contents"
  uses: satya-500/read-file-github-action@v1
  with:
    path: "package.json"
```

## Options ⚙️

The following input variables options can/must be configured:

|Input variable|Necessity|Description|Default|
|----|----|----|----|
|`path`|Required|the path to the file to read.||
|`encoding`|Optional|the encoding of the file to read.|`utf8`|

## Outputs
- `contents`: The contents of the file.

## Example

```yml
name: "Read file contents"

on: [push, pull_request]

jobs:
  file_contents:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v1

      - name: Read file contents
        id: read_file
        uses: satya-500/read-file-github-action@v1
        with:
          path: "package.json"

      - name: File contents
        run: echo "${ steps.read_file.outputs.contents }"
```
