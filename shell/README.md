# Shell script

## Why shell script

shell scripting can be used to build up automatic tools which performs duplicate works

### Test operator

`[]` is the test operator of shell script, it will return either true or false based on expression in it.

### Variables

Variables are name-value pairs, case sensitive, by convention are all uppercase, e.g.
Variables can be categorized to `local variable`, `environment variable` and `shell variable`

#### Declare a variable

`MY_VARIABLE="Value"`

#### Use a variable

`$MY_VARIABLE`

#### readonly variable

Make variable not changeable `readonly MY_VARIABLE`

#### Special variables

| Symbol  | Meaning  |
|---|---|
| $$ | pid of current process |
| $0 | filename of the current script |
| $n | variables correspond to the arguments with which script was invoked |
| $# | total number of parameters |
| $? | exit status or return of previous command |

#### Array of variables

    array_name[0]="TOM"
    array_name[1]="JERRY"
    array_name[2]="BROWN"

`array_name={"TOM", "JERRY", "BROWN"}`

To access values, use
`${array_name[index]}`

To access all values, use
`${array_name[*]}`

#### default variable

`echo ${var:-"Variable is not set"}`

### Shell operators

#### Arithmetic operator

+,-,*,/,%,=

will return calculating result

==.!=
`[ $a == $b ]` will return true of false

#### Relational operator

| Operator | Desc |
|---|---|
| -eq | check if value are equal |
| -ne | check if value are not equal |
| -gt | check if left value is greater than right value |
| ...

#### Boolean operator

| Operator | Desc |
| --- | --- |
| ! | invert true into false and vice versa |
| -o | or |
| -a | and |

e.g.

`[ $a -it 20 -a $ a -gt 10 ]`

#### String operator

| Operator | Desc |
| --- | --- |
| = | check if two string are equal |
| != | check if two string are not equal |
| -z | check if given string size is zero |
| -n | check if given string size is not zero |
| str | check if str is not empty |

#### File operator

Check status of files, refer to [file operator](https://www.tutorialspoint.com/unix/unix-basic-operators.htm)

### Decision making

Shell supports if...else statement by

- if...fi
- if...else...fi
- if...elif...else...fi  

e.g.

    #!/bin/sh
    if [ $1 = "hi" ]
    then
        echo "hi"
    elif [[ $1 = "ho" ]]
    then
        echo "ho"
    else
        echo "other word $1"
    fi

### Shell loop types

#### while loop

    while [condition]
    do
        ...
    done

#### break and continue

`break` can be used to exit a loop
`continue` can be used to exit the current iteration and execute the next iteration in loop

#### for loop

    NUMS = "1 2 3 4 5"
    for NUM in $NUMS
    do
        ...
    done

### Shell I/O

#### output redirection

`command/script > file` will output the result of command or script to file instead of terminal

#### input redirection

`command < file` will input content in file as arguments to the command

#### here document

`<<` here document is used to redirect input into an interactive shell or program.

`command << delimiter` here the shell interprets the `<<` as an instruction to read input until it finds a line contains the `delimiter`. The delimiter tells the shell that the here document has completed.

`<<' can be used to accept multi-line input until it find the ending delimiter.

#### Discard the output

`command > /dev/null` will just discard the output, `/dev/null` is a special file that automatically discards all inputs

`$ command > /dev/null 2>&1`, `1` represent `STDOUT` and `2` represent `STDERR`. The command will merge  `STDERR` stream to `STDOUT` stream, and `STDOUT` is set to discard output to `/dev/null`

### Functions

declare a function
    function_name () {
        commands...
        ... $1 -- use argument in function
        return val
    }
