Sure! Here’s a `README.md` file explaining your Makefile and how to use it.

---

# Neural Network Profiler

This project contains a simple neural network (`nn.c`) and a Makefile for compiling, running, and profiling the program using `gprof`.

## Prerequisites

Ensure you have the following installed on your system:

- **GCC** (GNU Compiler Collection)
- **gprof** (GNU Profiler)
- **gprof2dot** (for generating call graphs) *(optional)*
- **Graphviz** (`dot` command) *(optional, required for visualization)*

You can install missing dependencies using:

```sh
# Install required tools (Debian/Ubuntu)
sudo apt update && sudo apt install -y gcc gprof graphviz python3-gprof2dot

# Install required tools (Arch Linux)
sudo pacman -S gcc gprof graphviz python-gprof2dot
```

## Makefile Targets

### 1. Build and Run

To compile and execute the program:

```sh
make
```

This:
- Creates the `bin/` directory if it doesn't exist.
- Compiles `nn.c` into `bin/nn.exe` with profiling enabled (`-pg` flag).
- Runs `bin/nn.exe`.

### 2. Profiling with `gprof`

To analyze performance using `gprof`, run:

```sh
make gprof
```

This:
- Runs `bin/nn.exe` to generate a profiling report (`gmon.out`).
- Moves `gmon.out` to `bin/`.
- Uses `gprof` to generate a human-readable profiling report (`prof_analysis/gprof_analysis.txt`).
- If `gprof2dot` and `dot` are available, generates a call graph (`prof_analysis/gprof_graph.png`).

### 3. Cleaning the Project

To remove compiled files and profiling data:

```sh
make clean
```

This deletes the `bin/` and `prof_analysis/` directories.

## Profiling Output

After running `make gprof`, you will find:

- **`prof_analysis/gprof_analysis.txt`**: Text-based profiling data from `gprof`.
- **`prof_analysis/gprof_graph.png`** *(if dependencies installed)*: A graphical call graph of function execution times.

## Notes

- If `gprof2dot` and `dot` are missing, the script will warn you and skip the graph generation step.
- Profiling results may vary between runs due to system activity.

---

