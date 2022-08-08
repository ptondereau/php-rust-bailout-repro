# Repostiry for reproducing bailout for PHP

## Requirements

- Valgrind
- Rust + CLang
- PHP >= 8.0
- libc6-dbg

## Usage

```bash
# With extension
valgrind \
    --tool=memcheck \
    --leak-check=full \
    --num-callers=30 \
    --log-file=php_with_ext.log \
    php -dextension=target/debug/libphp_rs_valgrind.so index_with_ext.php

# Without extension
valgrind \
    --tool=memcheck \
    --leak-check=full \
    --num-callers=30 \
    --log-file=php_without_ext.log \
    php index_without_ext.php

```

## Pull request
https://github.com/davidcole1340/ext-php-rs/pull/145