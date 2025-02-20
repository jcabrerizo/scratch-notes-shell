# Variables

> bash/zsh fu question / tip - how to tell an unset variable, NOT matching an empty variable?
> I've always done `[[-z "${var}" ]]` which treats empty and unset the same, but ideally our build scripts will take a
> configurable -- possibly empty -- qualifier, default to a date stamp if not set, but leave blank if explicitly set
> blank, so that doesn't work!)
> answer relies on `+` -- `${var+override}` which returns override if var is set (including blank), or empty if unset; as
> follows:

```shell
% if [[ -n "${var+anything}" ]] ; then echo set ; else echo unset ; fi
unset
% if [[ -z "${var+anything}" ]] ; then echo unset ; else echo set ; fi
unset
```

```shell
% var=something
% if [[ -n "${var+anything}" ]] ; then echo set ; else echo unset ; fi
set
% if [[ -z "${var+anything}" ]] ; then echo unset ; else echo set ; fi
set
```

```shell
% unset var 
% if [[ -n "${var+anything}" ]] ; then echo set ; else echo unset ; fi
unset
% if [[ -z "${var+anything}" ]] ; then echo unset ; else echo set ; fi
unset
```

```shell
% var=
% if [[ -n "${var+anything}" ]] ; then echo set ; else echo unset ; fi
set
% if [[ -z "${var+anything}" ]] ; then echo unset ; else echo set ; fi
set
```

## Bash variable syntax

Show message error if var not defined using `:?error message`:

```shell
echo ${VARIABLE_NAME:?please set VARIABLE_NAME}
```