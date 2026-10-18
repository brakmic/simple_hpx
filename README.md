# Minimal HPX Demo

![CI](https://github.com/brakmic/simple_hpx/actions/workflows/ci.yml/badge.svg)

This project is a minimal demo to help new users get familiar with the HPX library. It demonstrates how to use HPX's core functionality, including asynchronous output (`hpx::cout`). The program prints "The answer is 42!" to the console using HPX's parallel execution engine.

## What is HPX?

HPX is a C++ Standard Library for concurrency and parallelism, enabling distributed and asynchronous computing. HPX provides a unified API for local and distributed execution, making it ideal for applications that require high performance, scalability, and parallelism.

This project uses HPX's `hpx_main` to handle the underlying runtime initialization, allowing developers to focus directly on the code logic without worrying about manually managing the HPX runtime.

## Project Structure

- **`simple_hpx.cpp`**: The main source file that prints `"The answer is 42!"` using HPX's asynchronous output capabilities (`hpx::cout`).
- **`CMakeLists.txt`**: The CMake configuration file that sets up the project, including the necessary HPX and Boost libraries.

## Prerequisites

- Docker.
- The demo builds inside `brakmic/hpx-builder:1.11.0`, which provides HPX
  1.11.0, Boost 1.83, GCC 13, and CMake 3.28. A local HPX installation also
  works with CMake 3.15+ and a C++23 compiler.

## Build Instructions

Build inside the builder image:

```bash
docker run --rm -it -v "$PWD:/src" brakmic/hpx-builder:1.11.0 /bin/bash
```

Inside the container:

```bash
cmake -S /src -B /src/build -DCMAKE_PREFIX_PATH=/usr/local/hpx
cmake --build /src/build --parallel 2
/src/build/simple_hpx
```

A one-shot build and run:

```bash
docker run --rm -v "$PWD:/src:ro" brakmic/hpx-builder:1.11.0 bash -lc '
  cp -a /src /tmp/app
  cmake -S /tmp/app -B /tmp/app/build -DCMAKE_PREFIX_PATH=/usr/local/hpx
  cmake --build /tmp/app/build --parallel 2
  /tmp/app/build/simple_hpx
'
```

You should see the following output:

```text
The answer is 42!
```

## License

[MIT](./LICENSE)
