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

6. For graphical applications, you need to forward X, check [this](https://virtualizationreview.com/articles/2018/01/30/hands-on-with-wsl-graphical-apps.aspx) out. After installing any X client, execute `export DISPLAY=:0`



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
3. [Pycharm tricks from zhihu](https://zhuanlan.zhihu.com/p/60383815) (Chinese)
4. Specify TeX compiler in your document, add `!TEX TS-program = lualatex`
5. Working with vtk file format, check [this](https://vtk.org/wp-content/uploads/2015/04/file-formats.pdf) out.
6. Linux is case-sensitive but Windows is not, it may cause problem with cross-platform code. [Here](https://www.howtogeek.com/354220/how-to-enable-case-sensitive-folders-on-windows-10/) is a solution to make windows folders case-sensitive.



## Misc troubleshooting

1. WSL doesn't start on win10. [Solution](https://superuser.com/questions/1275505/wsl-bash-doesnt-start)
2. `xelatex` running slow. Try to delete `texlive/${version}/texmf-var/fonts/cache`
3. 