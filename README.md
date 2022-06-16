# XV6-RISCV

## Original README
See [Orignal README](https://github.com/Aneureka/xv6-riscv/blob/riscv/ORIGINAL_README).

## Notes
1. Use [compiledb](https://github.com/nickdiego/compiledb) or [bear](https://github.com/rizsotto/Bear/) to generate `compile_commands.json`
2. Add `#pragma once` macro to all the header files
    ```shell
    echo "#pragma once\n" > /tmp/head.txt
    for file in $(find . -name "*.h"); do
        cat /tmp/head.txt $file > $file.modified
        mv $file.modified $file
    done
    ```
3. Add missing headers like `types.h`
4. Use `clang-format` to format source codes
    ```shell
    find . -name "*.[c|h]" -exec clang-format -i {} \;
    ```

## Recommended Courses
1. [NJU OS 2022](https://jyywiki.cn/OS/2022/) - learning 🥳
2. [6.S081 Fall 2021](https://pdos.csail.mit.edu/6.828/2021/)
