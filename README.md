# replace-between

CLI utility for replacing text between markers with text from a file or stdin.

# Usage

```
replace-between --source API.md --target README.md --token API
```

# Example

To put API in your `README.md`, you can put text generated by `jsdoc2md` between `<!--- API BEGIN --->` and `<!--- API END --->`.  

```
$ jsdoc2md index.js | replace-between --target README.md --token API
```

A sample `README.md` for above command could be as below: 

```md
# My Module

Lovely description.

# Details

Details of my module

# API

<!--- API BEGIN --->


<!--- API END --->
```


# Options

| Option  | Req |Description |
|:--------|:----|------------|
| token   |  ✓  | Token text to look for between start and end comment. BEGIN and END words are added automatically. |
| target  |  ✓  | Target file to replace text in. |
| source  |     | Source file to get replacement text from. If not provided STDIN is used instead. |
| comment |     | Predefined comment types to be used for replacement markers. (i.e. 'markdown' for `<!---` `--->`. If not provided, it is tried to be get from target file extension. |
| begin   |     | Beginning of the comment syntax. i.e `<!---` for markdown. |
| end     |     | End of the comment syntax. i.e `--->` for markdown. |

# Predefined Comment Strings

Predefined open and close tags are used for known file extensions if they are not overridden by `begin`, `end` or `comment` options. 

| Extension | Name        | Open    | Close  |
|-----------|-------------|---------|--------|
| md        | Markdown    | `<!---` | `--->` |
| js        | Javascript  | `/*`    | `*/`   |
| html      | HTML        | `<!--`  | `-->`  |
| css       | CSS         | `/*`    | `*/`   |
