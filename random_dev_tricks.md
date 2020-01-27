## Random Pro-tips

1. Select venv in Jupyter notebook: `conda install nb_conda_kernels`;

2. [Maya install numpy](https://forums.autodesk.com/t5/maya-programming/guide-how-to-install-numpy-scipy-in-maya-windows-64-bit/td-p/5796722): unzip whl file and copy the folder to `%MAYA_INSTALL_DIR%\Python\Lib\site-packages`;

3. [Pycharm tricks from zhihu](https://zhuanlan.zhihu.com/p/60383815) (Chinese);

4. Specify TeX compiler in your document, add `!TEX TS-program = lualatex`. This directive is understood by most TeX IDEs. More TeX directives see [here](https://tex.stackexchange.com/questions/78101/when-and-why-should-i-use-tex-ts-program-and-tex-encoding);

5. Working with vtk file format, check [this](https://vtk.org/wp-content/uploads/2015/04/file-formats.pdf) out;

6. Setup `cron` on WSL:

   ```bash
   # Check if cron is install
   dpkg -l cron
   # start cron service (systemctl won't work on WSL)
   sudo service cron status
   sudo service cron start
   # Setup cron tasks
   crontab -e
   ```

7. While annotating a codebase (C++ for example), in Visual Studio, change color of `XML Doc Comment` (in Tools->Options->Environment->Fonts and Colors). Start annotation using `///` instead of regular comment `//`;

8. How to set up CUDA integration in existing Visual Studio project:

   1. right click project -> build dependencies -> build customizations, check CUDA [link]( https://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/index.html#build-customizations-for-existing-projects )
   2. check environmental variables (should automatically be set when CUDA was installed correctly)
   3. set up C/C++ additional include directories: `$(ProjectDir)\include;$(IncludePath);$(CudaToolkitDir)include`
   4. set up linker: additional library directories: `%(AdditionalLibraryDirectories);$(CudaToolkitLibDir)`
   5. set up linker: additional dependencies, add cublas.lib;cudart_static.lib
   6. right click your file containing kernel code, in `properties -> general`, set the item type to `CUDA C/C++`
   7. for CUBLAS users, set CUDA C/C++ -> common, set target machine to `64-bit (--machine 64)`
   8. ` #include "device_launch_parameters.h"` to fix intellisense issues with CUDA



## Misc troubleshooting

1. WSL doesn't start on win10. [Solution](https://superuser.com/questions/1275505/wsl-bash-doesnt-start);

2. `xelatex` running slow. Try to delete `texlive/${version}/texmf-var/fonts/cache;`

3. If debugger fails to stop at breakpoint, maybe you forgot to generate debugging symbol (duh..., to verify this, use [objdump](https://stackoverflow.com/questions/3284112/how-to-check-if-program-was-compiled-with-debug-symbols));

4. Linux is case-sensitive but Windows is not, it may cause problem with cross-platform code. [Here](https://www.howtogeek.com/354220/how-to-enable-case-sensitive-folders-on-windows-10/) is a solution to make windows folders case-sensitive

5. Fix git connection issues on WSL:

   ```
   touch ~/.ssh/config
   chmod 755 ~/.ssh/config
   sudo nano ~/.ssh/config
   # add the following to this config
   Host github.com
     Hostname ssh.github.com
     Port 22
     
   # restart ssh
   sudo /etc/init.d/ssh restart
   # verify
   ssh -T git@github.com
   ```

   



## Copy-and-paste programming from Stackoverflow

1. Find and replace a string in multiple files using `find` and `sed` (note the trailing `\;`):

```
find /home/user/directory -name \*.c -exec sed -i "s/cybernetnews/cybernet/g" {} \;
```



## Misc.

### Configure VS Code for Linux C++ Project

Ref:

[Using C++ and WSL in VS Code](https://code.visualstudio.com/docs/cpp/config-wsl)

[Developing in WSL](https://code.visualstudio.com/docs/remote/wsl)

[Target Debugging and Launching](https://vector-of-bool.github.io/docs/vscode-cmake-tools/debugging.html)

[Quick Start to Use Visual Studio Code for C++ Programmers in Linux](https://www.codeproject.com/Articles/1184735/Quick-Start-to-Use-Visual-Studio-Code-for-Cplusplu)

[C++ Development using Visual Studio Code, CMake and LLDB](https://medium.com/audelabs/c-development-using-visual-studio-code-cmake-and-lldb-d0f13d38c563)

Steps:

1. Install VS Code extensions: WSL remote development, C/C++ extension **in Windows**;
2. Configure WSL:

```
sudo apt-get update
sudo apt-get install build-essential gdb cmake
sudo apt-get install freeglut3  freeglut3-dev binutils-gold libglew-dev mesa-common-dev libglew1.5-dev libglm-dev #OpenGL optional
```

3. Install X client (`xming` for example, then forward X using `export DISPLAY=:0`; a modern X client is [mobaxterm](https://mobaxterm.mobatek.net/features.html)

4. Configure `launch.json` for your project;

5. In **WSL**, from project folder, type `code .`.

   

### Useful Configs
#### git

```
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status

# For cross-platform between windows and POSIX systems
git config --global core.autocrlf true
```

#### sublime

```
{
	"font_size": 13,
    "word_wrap": "true",
    "match_brackets_angle": true // especially for dealing with ugly stl output...
}
```

