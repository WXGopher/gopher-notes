## Configure VS Code for Linux C++ Project

#### Ref:

[Using C++ and WSL in VS Code](https://code.visualstudio.com/docs/cpp/config-wsl)

[Developing in WSL](https://code.visualstudio.com/docs/remote/wsl)

[Target Debugging and Launching](https://vector-of-bool.github.io/docs/vscode-cmake-tools/debugging.html)

[Quick Start to Use Visual Studio Code for C++ Programmers in Linux](https://www.codeproject.com/Articles/1184735/Quick-Start-to-Use-Visual-Studio-Code-for-Cplusplu)

[C++ Development using Visual Studio Code, CMake and LLDB](https://medium.com/audelabs/c-development-using-visual-studio-code-cmake-and-lldb-d0f13d38c563)



#### Steps:

1. Configure WSL:

   ```
   sudo apt-get update
   sudo apt-get install build-essential gdb cmake
   # OpenGL optional
   sudo apt-get install freeglut3  freeglut3-dev binutils-gold libglew-dev mesa-common-dev libglew1.5-dev libglm-dev 
   ```

2. Configure VS Code, install [CMake tools](https://marketplace.visualstudio.com/items?itemName=vector-of-bool.cmake-tools), [WSL remote development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack), and VS Code C/C++ extension

3. In WSL, from project folder, type `code .`

4. `F1` -> `CMake: build`

5. Use `CMake: debug` to debug, remember to configure `launch.json`, more details [here](https://vector-of-bool.github.io/docs/vscode-cmake-tools/debugging.html#debugging).



## Useful git Configs

```
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status

# For cross-platform between windows and POSIX systems
git config --global core.autocrlf true
```



## Random Pro-tips

1. Select venv in Jupyter notebook: `conda install nb_conda_kernels`
2. [Maya install numpy](https://forums.autodesk.com/t5/maya-programming/guide-how-to-install-numpy-scipy-in-maya-windows-64-bit/td-p/5796722): unzip whl file and copy the folder to `%MAYA_INSTALL_DIR%\Python\Lib\site-packages`