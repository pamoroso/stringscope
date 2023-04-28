# Stringscope

Stringscope is a tool to display a list of text the strings contained in a binary file, i.e. the sequences of printable characters longer than a minimum threshold of 4 characters. The program, which is written in and runs under [Medley Interlisp](https://interlisp.org), is similar to the Unix tool `strings`.

![Stringscope output window](https://raw.githubusercontent.com/pamoroso/stringscope/main/stringscope.png)


## Installation

Download the file `STRINGSCOPE` from the project repo, copy it to a file system location your Medley Interlisp installation has access to, and optionally compile the source by evaluating the following expression from the Lisp executive:

```
(TCOMPL 'STRINGSCOPE)
```

Provide these answers to the questions the compiler asks:

* listing? no
* redefine? yes
* save exprs? no

Finally, to load the program evaluate:

```lisp
(FILESLOAD STRINGSCOPE)
```


## Usage

Once Stringscope is loaded you can call the following functions and commands.


### `STRINGSCOPE`

To run the program evaluate:

```lisp
(STRINGSCOPE FILENAME MIN.LEN)
```

where `FILENAME` is a file name and `MIN.LEN` the optional minimum length printable character sequences must have. The default is 4 characters but is user-configurable by changing the global variable `SSCOPE.MIN.LEN`. 

`STRINGSCOPE` prompts to create a window to display the output, which is scrollable. The output window has a prompt area attached to the top side and a menu to the right side. The prompt area serves for requesting input and displaying status messages, the menu contains the following items and subitems:

- `Get`: reads the strings of a new file
- `Find`: searches for strings matching a specific text
- `Sort`: sorts the strings in the following order
  * `Ascending`
  * `Descending`
- `Min Len`: changes the minimum length strings must have
- `Reset`: redisplays the strings read from the current file
- `Exit`: quits the program

The function returns the output window if the file is processed with no issues, `NIL` otherwise.


### `STRINGS`

To make the program print the strings to the primary output stream call the function `STRINGS`, which takes the same arguments as `STRINGSCOPE` and the additional optional argument `NEWWIN`:

```lisp
(STRINGS FILENAME MIN.LEN NEWWIN)
```

If `NEWWIN` is not `NIL`, `STRINGS` works exactly like `STRINGSCOPE` and displays the output in a new window. Depending on the value of `NEWWIN`, `STRINGS` returns the primary output stream or the new window if the file is processed with no issues, `NIL` otherwise.

`STRINGS` is available also as an Executive command which accepts the same first two arguments and prints the output:

```
STRINGS FILENAME MIN.LEN
```

### `EXTRACT.STRINGS`

The function:

```lisp
EXTRACT.STRINGS STREAM MIN.LEN
```

returns a list of the strings of at least `MIN.LEN` characters read from `STREAM`. The function assumes the input stream is already open.


## Release history

See the [list of releases](https://github.com/pamoroso/stringscope/releases) for notes on the changes in each version.


## Learn more

- [Stringscope project updates](https://write.as/paoloamoroso/tag:stringscope)
- [`strings`](https://en.wikipedia.org/wiki/Strings_(Unix))
- [Medley Interlisp](https://interlisp.org)


## Author

Stringscope is developed by [Paolo Amoroso](https://github.com/pamoroso).


## License

This code is distributed under the MIT license, see the `LICENSE` file.
