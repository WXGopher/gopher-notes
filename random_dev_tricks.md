## Configure VS Code for Linux C++ Project

### Ref:

[Using C++ and WSL in VS Code](https://code.visualstudio.com/docs/cpp/config-wsl)

[Developing in WSL](https://code.visualstudio.com/docs/remote/wsl)

[Target Debugging and Launching](https://vector-of-bool.github.io/docs/vscode-cmake-tools/debugging.html)

[Quick Start to Use Visual Studio Code for C++ Programmers in Linux](https://www.codeproject.com/Articles/1184735/Quick-Start-to-Use-Visual-Studio-Code-for-Cplusplu)

[C++ Development using Visual Studio Code, CMake and LLDB](https://medium.com/audelabs/c-development-using-visual-studio-code-cmake-and-lldb-d0f13d38c563)



### VS Code extensions:

[CMake tools](https://marketplace.visualstudio.com/items?itemName=vector-of-bool.cmake-tools), [WSL remote development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack), VS Code C/C++ extension



### Configure WSL:

```
sudo apt-get update
sudo apt-get install build-essential gdb cmake
# OpenGL optional
sudo apt-get install freeglut3  freeglut3-dev binutils-gold libglew-dev mesa-common-dev libglew1.5-dev libglm-dev 
```



### Steps:

1. In WSL, from project folder, type `code .`
2. `F1` -> `CMake: build`
3. Use `CMake: debug` to debug, remember to configure `launch.json`



## Useful git configs

```
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status

# For cross-platform between windows and POSIX systems
git config --global core.autocrlf true
```

