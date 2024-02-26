# Boost Windows Error

## Error

```sh
...
[build] [OMITTED]\boost\libs\winapi\include\boost/winapi/handles.hpp(50): error C2039: 'CompareObjectHandles': is not a member of '`global namespace''
[build] [OMITTED]\boost\libs\winapi\include\boost/winapi/handles.hpp(50): error C2873: 'CompareObjectHandles': symbol cannot be used in a using-declaration
...
```

## Requirements

| **Name**       | **Homepage**                         | **Notes**        |
| -------------- | ------------------------------------ | ---------------- |
| `CXX Compiler` | <https://visualstudio.microsoft.com> | `MSVC 14.0 2015` |
| `CMake`        | <https://cmake.org>                  | _`>= 3.14`_      |

### Build Options

| **Name**            | **Description**                                                             | **Type** | **Default** | **Notes**                                                                                                           |
| ------------------- | --------------------------------------------------------------------------- | -------- | ----------- | ------------------------------------------------------------------------------------------------------------------- |
| `CMAKE_BUILD_TYPE`  | Specifies the build type: <br/> <ul><li>`Debug`</li><li>`Release`</li></ul> | `STRING` | `Debug`     | See [CMake documentation](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html) for more information  |
| `BUILD_SHARED_LIBS` | Build shared libraries                                                      | `BOOL`   | `FALSE`     | See [CMake documentation](https://cmake.org/cmake/help/latest/variable/BUILD_SHARED_LIBS.html) for more information |

## Build

1. Generate project

    > **Note**: Change build options' values as needed

    ```sh
    cmake \
        -S . \
        -B ./build \
        -DCMAKE_BUILD_TYPE:STRING=Release \
        -DBUILD_SHARED_LIBS:BOOL=FALSE
    ```

1. Build project

    > **Note**: Change value of `--config` to match value of `CMAKE_BUILD_TYPE`

    ```sh
    cmake \
        --build ./build \
        --config Release
    ```
