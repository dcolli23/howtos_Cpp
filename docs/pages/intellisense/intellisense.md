---
title: Intellisense
nav_order: 2
---

# Intellisense

## For ROS Packages

To get intellisense in VS Code working with a ROS package, it's easiest to add the CMake flag, `-DCMAKE_ENABLE_COMPILE_COMMANDS=1` to your `catkin build` step. This outputs a file in `catkin_ws/build/<package_name>` that intellisense can use to discover everything in the package.

To do this:
1. Build your package with the CMake flag described above.
2. Open your package folder in VS Code.
3. Create a file named "c_cpp_properties.json". This should look something like:
    ```json
    {
        "configurations": [
            {
                "name": "Linux",
                "defines": [],
                "compilerPath": "/usr/bin/gcc",
                "cStandard": "gnu17",
                "cppStandard": "gnu++14",
                "intelliSenseMode": "linux-gcc-x64"
            }
        ],
        "version": 4
    }
    ```
4. Add the "complieCommands" key under the configuration where the value points to your newly created compile commands file. An example of what this would look like:
    ```json
    {
        "configurations": [
            {
                "name": "Linux",
                "defines": [],
                "compilerPath": "/usr/bin/gcc",
                "cStandard": "gnu17",
                "cppStandard": "gnu++14",
                "intelliSenseMode": "linux-gcc-x64",
                "compileCommands": "${workspaceFolder}/../build/cdcpd/compile_commands.json"
            }
        ],
        "version": 4
    }
    ```