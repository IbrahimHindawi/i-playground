# i-playground

Small I language playground project.

## Dependencies

- Python 3
- CMake
- Ninja
- LLVM/Clang with `clang-cl`
- `I.exe` on `PATH`, usually from `C:\devel\i-windows-x64`
- `std` beside `I.exe`, copied by the I compiler build to `C:\devel\i-windows-x64\std`

## Build And Run

```powershell
python bunyan.py run debug
```

Bunyan runs:

```text
I.exe compile src/main.i -> build/i_gen/main.c + build/i_gen/main.h
cmake config/build
build/i-playground.exe
```

The project imports the standard library through:

```i
import "std/Print.i"
```

`I.exe` resolves that through the `std` folder beside the compiler executable. Use Bunyan `i_import_dirs` only for project-local libraries.

Other configs:

```powershell
python bunyan.py build release
python bunyan.py build reldebug
python bunyan.py clean
```
