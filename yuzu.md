# Building for Windows

Tobias edited this page on Jun 20, 2023 · [54 revisions](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-for-Windows/_history)

# THIS GUIDE IS INTENDED FOR DEVELOPERS ONLY, SUPPORT WILL ONLY BE GIVEN IF YOU'RE A DEVELOPER.

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#this-guide-is-intended-for-developers-only-support-will-only-be-given-if-youre-a-developer)

## Method I: MSVC Build for Windows

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#method-i-msvc-build-for-windows)

### Minimal Dependencies

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#minimal-dependencies)

On Windows, all library dependencies are automatically included within the `externals` folder, or can be downloaded on-demand. To build yuzu, you need to install:

- **[Visual Studio 2022 Community](https://web.archive.org/web/20240302183850/https://visualstudio.microsoft.com/downloads/)** - **Make sure to select C++ support in the installer. Make sure to update to the latest version if already installed.**
- **[CMake](https://web.archive.org/web/20240302183850/https://cmake.org/download/)** - Used to generate Visual Studio project files. Does not matter if either 32-bit or 64-bit version is installed.
- **[Vulkan SDK](https://web.archive.org/web/20240302183850/https://vulkan.lunarg.com/sdk/home#windows)** - **Make sure to select Latest SDK.**

![2](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/e9b4203a1491c1c0d433b97c8d17e51144e34bdde05b8fb33b82a075872ce1af/68747470733a2f2f692e696d6775722e636f6d2f6769447775546d2e706e67)

- **Git** - We recommend [Git for Windows](https://web.archive.org/web/20240302183850/https://gitforwindows.org/).

![3](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/5071aa51bc44bb9c8ade83ce41607642bac7dc9c049f511ac823812df79e4c1e/68747470733a2f2f692e696d6775722e636f6d2f5565537a6b42772e706e67)

- While installing Git Bash, you should tell it to include Git in your system path. (Choose the "Git from the command line and also from 3rd-party software" option.) If you missed that, don't worry, you'll just have to manually tell CMake where your git.exe is, since it's used to include version info into the built executable.

![4](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/5bac078848b163baf8425aa33a7364a6859023861d05e024127f8be29ae29650/68747470733a2f2f692e696d6775722e636f6d2f783072527331742e706e67)

### Cloning yuzu with Git

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#cloning-yuzu-with-git)

**Master:**

```batchfile
git clone --recursive https://github.com/yuzu-emu/yuzu.git
cd yuzu
```

**Mainline (no assert):**

```batchfile
git clone --recursive https://github.com/yuzu-emu/yuzu-mainline.git
cd yuzu-mainline
```

![9](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/1f4381c1c994c1abf89d9c0808ef284bfb2193e33b8281b18ac08f84ceb5f31b/68747470733a2f2f692e696d6775722e636f6d2f436378494168742e706e67)

- _(Note: yuzu by default downloads to `C:\Users\<user-name>\yuzu` (Master) or `C:\Users\<user-name>\yuzu-mainline` (Mainline)_

### Building

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#building)

- Open the CMake GUI application and point it to the `yuzu` (Master) or `yuzu-mainline` (Mainline) directory.
    
    ![10](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/6b5ee5ff3c5298e5f274cbdfe7fc781db9d11cc3f5684c1003a4bac9af1018a3/68747470733a2f2f692e696d6775722e636f6d2f714f736c4957762e706e67)
    
- For the build directory, use a `/build` subdirectory inside the source directory or some other directory of your choice. (Tell CMake to create it.)
    
    ![11](https://web.archive.org/web/20240302183850im_/https://private-user-images.githubusercontent.com/20753089/246957039-738efcab-0da6-44ce-889d-becf3712db10.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDk0MDUwMzAsIm5iZiI6MTcwOTQwNDczMCwicGF0aCI6Ii8yMDc1MzA4OS8yNDY5NTcwMzktNzM4ZWZjYWItMGRhNi00NGNlLTg4OWQtYmVjZjM3MTJkYjEwLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNDAzMDIlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjQwMzAyVDE4Mzg1MFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTZmN2Y4MzFmYmRkZDVlZTVjYmRlYTM2NzBjNmZmN2M2M2E2YWZhYTIwNTFmYzI2MTBiMWUwMDVlM2M1MDc4N2YmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.3hjvBm6bpBuWRLEg4KfNrJ5Qq_r218VDacd7gV_gbvY)
    
- Click the "Configure" button and choose `Visual Studio 17 2022`, with `x64` for the optional platform.
    
    ![12](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/195da4d9b1a4dff76b77fe5a95b9dfd66479fb932ecb4653c0f9ca47267184a3/68747470733a2f2f692e696d6775722e636f6d2f444b695245614b2e706e67)
    
    - _(Note: If you used GitHub's own app to clone, run `git submodule update --init --recursive` to get the remaining dependencies)_
- If you get an error about missing packages, enable `YUZU_USE_BUNDLED_VCPKG`, and then click Configure again.
    
    - _(You may also want to disable `YUZU_TESTS` in this case since Catch2 is not yet supported with this.)_
    
    ![13](https://web.archive.org/web/20240302183850im_/https://user-images.githubusercontent.com/22451773/180585999-07316d6e-9751-4d11-b957-1cf57cd7cd58.png)
    
- Click "Generate" to create the project files.
    
    ![15](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/2e25ff47cf5e54e53a0cac30cc256c98c1f97ec3f9c9e45b50dac89406329cf3/68747470733a2f2f692e696d6775722e636f6d2f354c4b6739326b2e706e67)
    
- Open the solution file `yuzu.sln` in Visual Studio 2022, which is located in the build folder.
    
    ![16](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/d914c4074c3bac7b8803d4cdd87a65f4f621d620599fcf143d79a5de8a5f640a/68747470733a2f2f692e696d6775722e636f6d2f323038794d6d6c2e706e67)
    
- Depending if you want a graphical user interface or not (`yuzu` has the graphical user interface, while `yuzu-cmd` doesn't), select `yuzu` or `yuzu-cmd` in the Solution Explorer, right-click and `Set as StartUp Project`.
    
    ![17](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/84e8c3a32f2d18817214aecdbddecf6e613b1d765bd9d337fce7920645d767da/68747470733a2f2f692e696d6775722e636f6d2f6e504d616a6e6e2e706e67) ![18](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/3db18f7ae619b8e18b54332a0ad949c29bd6cb401a7d38011576453057cd98c8/68747470733a2f2f692e696d6775722e636f6d2f42444d4c7a525a2e706e67)
    
- Select the appropriate build type, Debug for debug purposes or Release for performance (in case of doubt choose Release).
    
    ![19](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/dde8f49e5fb9945036534748e89537fc3ebdcc78c492e170ffa8bd9d8b90d92e/68747470733a2f2f692e696d6775722e636f6d2f71786734726f432e706e67)
    
- Right-click the project you want to build and press Build in the submenu or press F5.
    
    ![20](https://web.archive.org/web/20240302183850im_/https://camo.githubusercontent.com/c10e2425c124c2b8fc190286fd378a62910e4430338de07e7e5615cc769ea5a2/68747470733a2f2f692e696d6775722e636f6d2f436b51674f46572e706e67)
    

Feel free to ask us in the IRC channel #yuzu-emu @ [libera](https://web.archive.org/web/20240302183850/https://web.libera.chat/) or on [Discord](https://web.archive.org/web/20240302183850/https://discord.com/invite/u77vRWY) if you have issues.

## Method II: MinGW-w64 Build with MSYS2

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#method-ii-mingw-w64-build-with-msys2)

### Prerequisites to install

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#prerequisites-to-install)

- [MSYS2](https://web.archive.org/web/20240302183850/https://www.msys2.org/)
- [Vulkan SDK](https://web.archive.org/web/20240302183850/https://vulkan.lunarg.com/sdk/home#windows) - **Make sure to select Latest SDK.**
- Make sure to follow the instructions and update to the latest version by running `pacman -Syu` as many times as needed.

### Install yuzu dependencies for MinGW-w64

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#install-yuzu-dependencies-for-mingw-w64)

- Open the `MSYS2 MinGW 64-bit` (mingw64.exe) shell
- Download and install all dependencies using: `pacman -Syu git make mingw-w64-x86_64-SDL2 mingw-w64-x86_64-cmake mingw-w64-x86_64-python-pip mingw-w64-x86_64-qt5 mingw-w64-x86_64-toolchain autoconf libtool automake-wrapper`
- Add MinGW binaries to the PATH: `echo 'PATH=/mingw64/bin:$PATH' >> ~/.bashrc`
- Add glslangValidator to the PATH: `echo 'PATH=$(readlink -e /c/VulkanSDK/*/Bin/):$PATH' >> ~/.bashrc`

### Clone the yuzu repository with Git

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#clone-the-yuzu-repository-with-git)

```shell
git clone --recursive https://github.com/yuzu-emu/yuzu.git
cd yuzu
```

### Run the following commands to build yuzu (dynamically linked build)

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#run-the-following-commands-to-build-yuzu-dynamically-linked-build)

```shell
mkdir build && cd build
cmake -G "MSYS Makefiles" -DYUZU_USE_BUNDLED_VCPKG=ON -DYUZU_TESTS=OFF ..
make -j$(nproc)
# test yuzu out with
./bin/yuzu.exe
```

- _(Note: This build is not a static build meaning that you need to include all of the DLLs with the .exe in order to use it!)_

e.g.

```shell
cp externals/ffmpeg-*/bin/*.dll bin/
```

Bonus Note: Running programs from inside `MSYS2 MinGW x64` shell has a different %PATH% than directly from explorer. This different %PATH% has the locations of the other DLLs required. ![image](https://web.archive.org/web/20240302183850im_/https://user-images.githubusercontent.com/190571/165000848-005e8428-8a82-41b1-bb4d-4ce7797cdac8.png)

### Building without Qt (Optional)

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#building-without-qt-optional)

Doesn't require the rather large Qt dependency, but you will lack a GUI frontend:

- Pass the `-DENABLE_QT=no` flag to cmake

## Method III: CLion Environment Setup

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#method-iii-clion-environment-setup)

### Minimal Dependencies

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#minimal-dependencies-1)

To build yuzu, you need to install the following:

- [CLion](https://web.archive.org/web/20240302183850/https://www.jetbrains.com/clion/) - This IDE is not free; for a free alternative, check Method I
- [Vulkan SDK](https://web.archive.org/web/20240302183850/https://vulkan.lunarg.com/sdk/home#windows) - Make sure to select the Latest SDK.

### Cloning yuzu with CLion

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#cloning-yuzu-with-clion)

- Clone the Repository:

![1](https://web.archive.org/web/20240302183850im_/https://user-images.githubusercontent.com/42481638/216899046-0d41d7d6-8e4d-4ed2-9587-b57088af5214.png) ![2](https://web.archive.org/web/20240302183850im_/https://user-images.githubusercontent.com/42481638/216899061-b2ea274a-e88c-40ae-bf0b-4450b46e9fea.png) ![3](https://web.archive.org/web/20240302183850im_/https://user-images.githubusercontent.com/42481638/216899076-0e5988c4-d431-4284-a5ff-9ecff973db76.png)

### Building & Setup

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#building--setup)

- Once Cloned, You will be taken to a prompt like the image below:

![4](https://web.archive.org/web/20240302183850im_/https://user-images.githubusercontent.com/42481638/216899092-3fe4cec6-a540-44e3-9e1e-3de9c2fffc2f.png)

- Set the settings to the image below:
- Change `Build type: Release`
- Change `Name: Release`
- Change `Toolchain Visual Studio`
- Change `Generator: Let CMake decide`
- Change `Build directory: build`

![5](https://web.archive.org/web/20240302183850im_/https://user-images.githubusercontent.com/42481638/216899164-6cee8482-3d59-428f-b1bc-e6dc793c9b20.png)

- Click OK; now Clion will build a directory and index your code to allow for IntelliSense. Please be patient.
- Once this process has been completed (No loading bar bottom right), you can now build yuzu
- In the top right, click on the drop-down menu, select all configurations, then select yuzu

![6](https://web.archive.org/web/20240302183850im_/https://user-images.githubusercontent.com/42481638/216899226-975048e9-bc6d-4ec1-bc2d-bd8a1e15ed04.png)

- Now run by clicking the play button or pressing Shift+F10, and yuzu will auto-launch once built.

![7](https://web.archive.org/web/20240302183850im_/https://user-images.githubusercontent.com/42481638/216899275-d514ec6a-e563-470e-81e2-3e04f0429b68.png)

## Building from the command line with MSVC

[](https://web.archive.org/web/20240302183850/https://github.com/yuzu-emu/yuzu/wiki/Building-For-Windows#building-from-the-command-line-with-msvc)

```batchfile
git clone --recursive https://github.com/yuzu-emu/yuzu
cd yuzu
mkdir build
cd build
cmake .. -G "Visual Studio 17 2022" -A x64
cmake --build . --config Release
```