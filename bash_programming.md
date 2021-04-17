# Contents

  - [Parameter and Variables](#Parameter%20and%20Variables "wikilink")
  - [Testing an expressions](#Testing%20an%20expressions "wikilink")
  - [Shell script order and
    checklist](#Shell%20script%20order%20and%20checklist "wikilink")
  - [Wildcards](#Wildcards "wikilink")
  - [Named character classes](#Named%20character%20classes "wikilink")
  - [Logging](#Logging "wikilink")
  - [Debugging](#Debugging "wikilink")
  - [Manual Debugging](#Manual%20Debugging "wikilink")

## Parameter and Variables

<span id="Special Parameters:"></span>**Special Parameters:**

  - `$*` & `$@` : expand to the value of all the positional parameters
    combined.
  - `$#` : expands to the number of positional parameters.
  - `$0` : contains the path to the currently running script or to the
    shell itself if no script is being executed.
  - `$$` : contains the process identification number (PID) of the
    current process.
  - `$?` : is set to the exit code of the last executed command.
  - `$_` : is set to the last argument to that command.
  - `$!` : contains the PID of the last command executed in the
    background.
  - `$-` : is set to the option flags currently in effect.

## Testing an expressions

<span id="File operators:"></span>**File operators:**

  - `-d FILE` : true if file is a directory.
  - `-e FILE` : true if file exists.
  - `-f FILE` : true if file exists and is a regular file.
  - `-r FILE` : true if file is readable by you.
  - `-s FILE` : true if file exists and is not empty.
  - `-w FILE` : true if the file is writable by you.
  - `-x FILE` : true if the file is executable by you.

<span id="Example:"></span>**Example:**

> `[ -x $HOME/bin/hw ]` \#\# true if you can execute the file

<span id="Bash options:"></span>**Bash options:**

  - `-n noexec` : read commands in script, but do not execute them
    (syntax check)

## Shell script order and checklist

1.  Shebang
2.  Comments/file header
3.  Global variables
4.  Functions:
    1.  Use local variables
5.  Main script contents
6.  Exit with an exit status:
    1.  exit \<STATUS\> at various exit points

<span id="Example:"></span>**Example:**

> `#!/bin/bash` `#: Title : hw` `#: Date : 2020-08-07` `#: Author :
> "Alvaro Lupercio" <lupera1@jhuapl.edu>` `#: Version : 1.0` `#:
> Description : print Hello, World!` `#: Options : None`

## Wildcards

  - (\*) - matches zero or more characters.
      - \*.txt - all files that end in txt.
      - a\* - all files that start with the letter a.
      - a\*.txt - all files that start with the letter a and end in
        .txt.
  - ? - matches exactly one character.
      - ?.txt - all the files that have only one character preceding
        .txt
      - a? - all the two letter files that start with the letter a.
      - a?.txt - all the files that start with an are followed by
        exactly one more character and end in .txt.

## Named character classes

  - `[[:alpha:]]` - matches alphabetic letters (lower and uppercase)
  - `[[:alnum:]]` - matches alphanumeric characters (alpha and digits)
  - `[[:digit:]]` - matches numbers in decimal from 0 - 9
  - `[[:lower:]]` - matches any lower case letters
  - `[[:space:]]` - matches white space (spaces, tabs, and new line
    characters)
  - `[[:upper:]]` - matches uppercase characters

## Logging

<span id="Facilities:"></span>**Facilities:**

  - kern
  - user
  - mail
  - daemon
  - auth
  - local0
  - local7

<span id="Severities:"></span>**Severities:**

  - emerg
  - alert
  - crit
  - err
  - warning
  - notice
  - info
  - debug

## Debugging

  - `-x` - prints commands as they execute after substitutions and
    expansions. Called an x-trace, tracing, or print debugging.
  - `#!/bin/bash -x`
  - `set -x`:
      - set +x to stop debugging
  - `-e` - exit on error. can be combined with other options:
      - `#!/bin/bash -ex`
  - `-v` - prints shell input lines as they are read. can be combined
    with other options:
      - `#!/bin/bash -vx`

## Manual Debugging

  - You can create your own debugging mode.
  - Use a special variable like debug:
      - `DEBUG=true`
      - `DEBUG=false`
  - Exmples: `#!/bin/bash` `DEBUG=true` `$DEBUG && echo "Debug mode
    ON."` `#!/bin/bash` `DEBUG=false` `$DEBUG || echo "Debug mode OFF."`
