[ANSI escape codes](https://en.wikipedia.org/wiki/ANSI_escape_code) are a way to control a terminal emulator from the shell. They can be used to control the appearance of text, the cursor, and more. Fig uses ANSI escape codes to send data from the shell to Fig, such as the current directory and exit code of a command.

For this challenge, you will write a program that parses specific ANSI escape codes from a stream of text. The program should read the input a byte at a time and print the output as it is received, excluding the specific ANSI escape codes. The program should save the values of the ANSI escape codes to a file specified as an argument to the program.

The ANSI escape code that you should implement are the following, any other escape codes should be ignored and passed through to the output.

- `ESC[123;PWD;BEL` - The current working directory should be saved
to the file.
- `ESC[123;PRINT_ENV=<ENV>;BEL` - The value of the environment variable
`<ENV>` should be saved to the file. For example `PRINT_ENV=HOME` should
save the value of `HOME` to the file.

Notes:

- `ESC` is the escape character `0x1b`.
- `BEL` is the bell character `0x07`.

Example of input and output when running with an argument of `file.txt`

Input to `stdin`:

```
Hello, world!ESC[123;PWD;BEL More Text. ESC[123;PRINT_ENV=SHELL;BEL ESC[234;NO_OP;BEL Goodbye!
```

Output to `stdout`:

```
Hello, world! More Text. ESC[234;NO_OP;BEL Goodbye!
```

Output to `file.txt`:

```
/Users/user/
/bin/bash
```

## Deliverables

When you're ready to submit, please create a zip file of the items below:

- README.md - Include some details on your though process when creating the parser and any difficulties you had along the way
- All code for the project

If you are stuck on something, please reach out to us!

You get no points for guessing. We want you to succeed, if you are stuck, please get in touch!

## Rubric

We will evaluate your project based on:

1. Correctness: How well does the implementation work? What edge cases were considered?
2. Code quality and design: Does the code feel like idiomatic Rust/C/Go?
