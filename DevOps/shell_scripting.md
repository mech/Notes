# Shell Scripting

* [`set -e`](http://stackoverflow.com/questions/19622198/what-does-set-e-in-a-bash-script-mean)
* [Writing robust bash shell scripts](http://www.davidpashley.com/articles/writing-robust-shell-scripts/)
* [Some shell scripting for Docker](https://blog.relateiq.com/a-docker-dev-environment-in-24-hours-part-2-of-2/)
* [**Good to learn shell scripting for Docker**](http://ypereirareis.github.io/blog/2015/05/04/docker-with-shell-script-or-makefile/)

Shell scripting purpose is for the automation of a series of commands. We can execute most command in a shell script that we can from the command line.

Bash scripts are very good at:

* File manipulation
* Running programs
* Processing text

```
▶ bash --version

// See https://www.gnu.org/software/bash/manual/html_node/Special-Parameters.html

$0 - Positional argument, the program itself
$1 - Argument 1
$2 - Argument 2
$3 - Argument 3 and so on...

$* - All the arguments
$@ - All the arguments (same but with subtle difference)

$# - The count of arguments

$? - Print last error code. Most recent foreground pipeline exit status.

$! - PID of the most recent background command
$$ - PID of the current shell (not sub-shell)

$- - Current options set for the shell

// The ampersand give us back the prompt without waiting for it
▶ ./somelongwork &

// Run in order with semicolon
▶ pwd ; ls
```

* 600 - Read/Write by owner only
* 755 - Execute permission set. Same as a+x

## Variables
	
Good habit:

* Surround your variables with quotes: `"$x"`
* Use braces to denote where your variable name end: `"${foo}bar"`
* Use `$HOME` instead of `~`

```
NAME=mech
echo $NAME
echo ${NAME}
echo "$NAME"
echo "${NAME}"
echo ${NAME%e} # Take off the e character
▶ convert "$PIC" "${PIC%.jpg}.png"

dirname="${1%/*}"
basename="${1##*/}" // double # get the longest match

// Using double quote is always recommended
bindir="${HOME}/bin"

// Get the length of the string in a variable
${#var}```

## Command Substitution

```
date=$(date)
```

## I/O Redirection

```
/dev/stdin = 0
/dev/stdout = 1
/dev/stderr = 2
/dev/null

Since 2 is the specific stream number for error, you can do 2>, so:
▶ cmd 2> /dev/null # Will discard all errors

▶ 2>&1 # Redirects stderr into stdout

▶ ls -l data.txt > output.txt
▶ ls -l not.here 2> error.txt
▶ ls -l data.txt not.here &> both.txt
▶ ls -l data.txt not.here > output.txt 2>&1 # Order is important

▶ ls | wc # STDOUT is being pipe to STDIN to wc
```

`2>&1` is redirect standard error??

### HERE Document

Buffer until the next string `EOF` match.

```
▶ wc << EOF
> This is a test
> EOF
```

## Decisions

```
# Tests on files and directories
# [[...]] is a bash extension. No quotes needed around variables.
if [[ ! -d $VOLUME_HOME/mysql ]]; then
fi

# Arithmetic tests
if [[ $# -ne 2 ]]; then
  echo "Need exactly two arguments"
  exit 1
fi

# Do not use double equal and must have space
if [[ $1 = "cat" ]]; then
  echo "meow"
fi
```

```
▶ help [[
▶ help test
```

### While

```
while test; do
  ;;
done

until test; do
  ;;
done
```

### For loop



## Printf

```
▶ printf "|%20s |%20s |%20s |\n" $(ls)
```

## sed

```
sed -i -r "s/license key here/${1}" newrelic.js
```

Page 30