# Bash

## Random commands

### `declare`

Declare variables and give them attributes. If no names are given, then display the values of variables instead.

Also it shows the definition of functions using the flag `-f`

```shell
declare -f my_cool_function
```

### Search for regex in directories and extract unique results

In this example, searching for "Error" and "Exception" in lines including "import" and printing the unique imported
classes

```shell
egrep -r '(Error|Exception)' src annotation-generated-src | grep import | awk '{print $2}' | sort | uniq
```

> ```shell
> com.amazonaws.services.mqinternal.model.AmazonMQInternalException;
> com.amazonaws.services.mqinternal.model.BadRequestException;
> com.amazonaws.services.mqinternal.model.NotFoundException;
> ```

## Add multiple lines from the output of a command into file

Notice the escaped `\n` before the `eval` invocation for adding an extra line❗

```shell
echo '# Just a comment\neval "$(command)"' >> ~/.zshrc
```

## `for` loop in for repeat commands

```shell
for F in banana apple pear
do 
  echo $F
done
```

Using auto incremental with an optional variable increment `{START..END..INCREMENT}`

```shell
for I in {0..10..2}
do
  echo "Even number $I"
done
```

```shell
for I in {0..5}
do
  echo "Number $I"
done
```

Loop over an array of elements

```shell
AWS_ZONES=('us-east-2a' 'us-west-1a' 'eu-central-1a')
 
for Z in "${AWS_ZONES[@]}"
do
  echo "region: $Z" 
done
```

Infinite loop

```shell
for (( ; ; ))
do
   echo "infinite loops [ hit CTRL+C to stop]"
done
```

Loop through files

```shell
for F in ./*
do
  echo "Filename: $F"
done
```