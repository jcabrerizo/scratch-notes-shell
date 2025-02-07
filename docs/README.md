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

## Add multiple lines into file

```shell
echo '# Just a comment\neval "$(command)"' >> ~/.zshrc
```