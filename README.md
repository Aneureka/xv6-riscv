# XV6-RISCV

## Original README
See [Orignal README](https://github.com/Aneureka/xv6-riscv/blob/riscv/README).

## Notes
1. Use [compiledb](https://github.com/nickdiego/compiledb) or [bear](https://github.com/rizsotto/Bear/) to generate `compile_commands.json`
2. Add `#pragma once` macro to all header files
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
5. Configure `launch.json` and `tasks.json` for debugging
6. Change `CPUS` in `Makefile` to 1 for debugging

## Debug setup
Prerequisites:
- install required toolchains referring to  [Orignal README](https://github.com/Aneureka/xv6-riscv/blob/riscv/README)
- Change `CPUS` in `Makefile` to 1 for debugging

### Terminal
1. Run `make qemu-gdb` and you will see information belowed and `.gdbinit` created
    ```txt
    *** Now run 'gdb' in another window.
    qemu-system-riscv64 -machine virt -bios none -kernel kernel/kernel -m 128M -smp 3 -nographic -drive file=fs.img,if=none,format=raw,id=x0 -device virtio-blk-device,drive=x0,bus=virtio-mmio-bus.0 -S -gdb tcp::25000
    ```
2. Open another terminal and run `gdb-multiarch kernel/kernel`

### VSCode
1. Run `make qemu-gdb` and get `.gdbinit` file in current directory
2. Configure `launch.json` and `tasks.json` in `.vscode`
    - You can refer these two files in this repo
    - Replace `miDebuggerServerAddress` item with the specific value in `.gdbinit` generated in the last step
3. Click `F5` and comment `target remote 127.0.0.1:<port>` with `@REM remote 127.0.0.1:<port>`

## Recommended courses
1. [NJU OS 2022](https://jyywiki.cn/OS/2022/) - learning 🥳
2. [6.S081 Fall 2021](https://pdos.csail.mit.edu/6.828/2021/)
