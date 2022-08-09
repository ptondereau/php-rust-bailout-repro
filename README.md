# Repostiry for reproducing bailout for PHP

## Requirements

- Valgrind
- Rust + CLang
- PHP >= 8.0 in debug mode
- libc6-dbg

## Usage

```bash
# With extension
ZEND_DONT_UNLOAD_MODULES=1 valgrind \
    -s \
    --leak-check=full \
    --track-origins=yes \
    --show-reachable=yes \
    --num-callers=30 \
    --log-file=php_with_ext.log \
    --show-leak-kinds=all \
    $HOME/Code/php-debug/bin/php -dmemory_limit=2M -dextension=target/debug/libphp_rs_valgrind.so index_with_ext.php

# Without extension
ZEND_DONT_UNLOAD_MODULES=1 valgrind \
    --leak-check=full \
    -s \
    --track-origins=yes \
    --show-reachable=yes \
    --num-callers=30 \
    --log-file=php_without_ext.log \
    --show-leak-kinds=all \
    $HOME/Code/php-debug/bin/php -dmemory_limit=2M index_without_ext.php

```

## Pull request
https://github.com/davidcole1340/ext-php-rs/pull/145