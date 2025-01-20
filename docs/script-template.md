# Script template

From: # https://sharats.me/posts/shell-script-best-practices/

```bash
#!/usr/bin/env bash
# USAGE:
#    ./build.sh [option]

set -o errexit
set -o nounset
set -o pipefail

if [[ "${TRACE-0}" == "1" ]]; then
    set -o xtrace
fi

# Show help
if [[ "${1-}" =~ ^-*h(elp)?$ ]]; then
    echo 'Usage: ./script.sh arg-one arg-two

This is an awesome bash script to make your life better.

'
    exit
fi

cd "$(dirname "$0")"

main() {
    echo do awesome stuff
}

# Update number of commented lines on the top of the file
function help () {
    head -3 $0 | sed "/!\/bin\/bash/d" | sed -e "s/#//g"
}

main "$@"
```