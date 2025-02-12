# Shell functions

ref: https://www.gnu.org/software/bash/manual/html_node/Shell-Functions.html

## Syntax

```shell
functionName () {
 compound-command 
} [ redirections ]
```

## Commands

### Unset function

```shell
unset -f function_name
```

## Examples

```shell
copyPath(){
  pwd|pbcopy
}
```