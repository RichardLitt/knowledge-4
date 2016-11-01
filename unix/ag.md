# ag

A fast way to search through text files.

`ag [file-type] [options] PATTERN [PATH]`

# Example

```shell
# Finds files containing "hello"
ag hello

# Finds files containing "hello" in ~/code
ag hello ~/code

# Finds Elixir files containing "hello" in ~/code
ag --elixir hello ~/code
```

## File types

Flags to only search through specified file types. For example, `--html` only searches in HTML files.

See the supported file types with `ag --list-file-types`.

`ag` respects `.gitignore` files.

## Common options

* `-c` prints the number of matches in each file
* `-i` for case insensitivity
* `-l` only returns the filenames
* `-o` prints only the matching part of the lines
* `--stats` prints cool statistics
* `-z` searches the content of compressed files
* `-L` print names of files that don't contain matches  
