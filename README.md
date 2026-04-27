# bazel_test

A minimal C++ project demonstrating how to build an SDL3 application using the Bazel build system.

SDL3 is fetched from source and built as a static library using `rules_foreign_cc`, which drives SDL's CMake build from within Bazel.

## Prerequisites

### Bazelisk (recommended)
```bash
 go install github.com/bazelbuild/bazelisk@latest
 export PATH=$PATH:$(go env GOPATH)/bin
 alias bazel=bazelisk
```

### Linux system dependencies
```bash
 sudo apt install -y \
   build-essential cmake ninja-build \
   libx11-dev libxext-dev libxrandr-dev libxcursor-dev libxi-dev \
   libwayland-dev libxkbcommon-dev \
   libegl1-mesa-dev libgl1-mesa-dev \
   libpulse-dev libasound2-dev \
   libdbus-1-dev libsystemd-dev \
   libdrm-dev libgbm-dev
```

## Build

```bash
bazel build //src:my_sdl_app
```

## Run

```bash
./bazel-bin/src/my_sdl_app
```

A window titled "Hello SDL3" will appear for 2 seconds, then exit.

## Project Structure

```
.
├── MODULE.bazel              # Bzlmod dependencies (rules_cc, rules_foreign_cc, SDL3 source)
├── WORKSPACE.bazel           # Empty - Bzlmod is used
├── .bazelversion             # Pins Bazel 7.4.1
├── third_party/
│   └── sdl/
│       └── BUILD.bazel       # Wraps SDL3 CMake build as a static library
└── src/
    ├── BUILD.bazel           # cc_binary target
    └── main.cc               # Minimal SDL3 application
```
