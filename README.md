# intoc

Generate a markdown TOC for a README or any Github-Flavored-Markdown files.

<!-- toc -->
- [intoc](#intoc)
  - [Feature](#feature)
  - [Install](#install)
  - [Requirement](#requirement)
  - [CLI](#cli)
  - [Usage](#usage)
  - [FAQ](#faq)
  - [License](#license)
  - [Author](#author)

## Feature

- Python based.
- No WebAPI use.
- Multiple output ways.
  - Output to the stdout
  - Direct Update(Insert to the next of `<!-- toc -->` line directly).
- Support sections written in Japanese.

## Install

```
$ git clone https://github.com/stakiran/intoc
```

And create a alias to `python intoc.py -i (TargetMarkdownFile)` if needed.

## Requirement

- Python 2.7
- Windows 7+
  - Maybe works on Linux, but not tested yet.

## CLI

```
$ python intoc.py -h
usage: intoc.py [-h] -i INPUT [--indent-depth INDENT_DEPTH]
                [--parse-depth PARSE_DEPTH] [--use-asterisk] [--edit]
                [--edit-target EDIT_TARGET]

optional arguments:
  -h, --help            show this help message and exit
  -i INPUT, --input INPUT
                        A input filename. (default: None)
  --indent-depth INDENT_DEPTH
                        The number of spaces per a nest in TOC. (default: 2)
  --parse-depth PARSE_DEPTH
                        The depth of the TOC list nesting. If minus then no
                        limit depth. (default: -1)
  --use-asterisk        Use an asterisk `*` as a list grammer. (default:
                        False)
  --edit                If given then insert TOC to the file from "--input".
                        (default: False)
  --edit-target EDIT_TARGET
                        A insertion destination label when --edit given. NOT
                        CASE-SENSITIVE. (default: <!-- TOC)
```

## Usage

Sample markdown file.

```
$ type intoc.md
# intoc
Generate a markdown TOC for a README or any GFM files.

<!-- toc -->

## Install
...

## CLI
..

## Info
...

### License
...

### Author
...
```

If no other option, output to the stdout.

```
$ python intoc.py -i README.md
- [intoc](#intoc)
  - [Install](#install)
  - [CLI](#cli)
  - [Info](#info)
    - [License](#license)
    - [Author](#author)
```

Use depth options.

```
$ python intoc.py -i README.md --indent-depth 4 --parse-depth 2
- [intoc](#intoc)
    - [Install](#install)
    - [CLI](#cli)
    - [Info](#info)
```

Use asterisk.

```
$ python intoc.py -i README.md --use-asterisk
* [intoc](#intoc)
  * [Feature](#feature)
  * [Install](#install)
  * [Requirement](#requirement)
  * [CLI](#cli)
  * [Usage](#usage)
  * [FAQ](#faq)
  * [License](#license)
  * [Author](#author)
```

Direct update the input file.

```

$ python intoc.py -i README.md --edit

$ type README.md
# intoc
Generate a markdown TOC for a README or any GFM files.

<!-- toc -->
- [intoc](#intoc)
  - [Install](#install)
  - [CLI](#cli)
  - [Info](#info)
    - [License](#license)
    - [Author](#author)

## Install
...
```

## FAQ

- Q: Is it possible to use intoc about any extension?
  - Ans: Possible. Use `--md-guard-break` option.
  - By default, intoc accepts only `.md` files.

## License

[MIT License](LICENSE)

## Author

[stakiran](https://github.com/stakiran)
