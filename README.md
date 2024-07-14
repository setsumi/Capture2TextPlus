# Capture2TextPlus

Windows mod of Capture2Text, code sync from: https://sourceforge.net/projects/capture2text/

## Download

https://github.com/setsumi/Capture2TextPlus/releases

## Changes

- option "Output->Save captured image" saves properly cut image including some padding
- hot key cycle of text orientation goes between Horizontal and Vertical ignoring Auto
- do not perform OCR if no text output is specified
- updated to tesseract/5.4.1 from [here](https://conan.io/center/recipes?value=tesseract)

## Dependencies

Tesseract, Qt 5 (cannot be version 4), Leptonica ([full list](https://github.com/setsumi/Capture2TextPlus/raw/master/conanfile.txt))

## Build instructions

Auto build by Github Actions.

### Manual build:
1. Install Visual Studio 2019 with C++ toolchain
2. Install Git for Windows
3. Install Qt Creator
4. Install Python 3.10
5. Enable option: Windows Control panel->Region->Administrative->Change system locale...->"Beta: Use Unicode UTF-8 for worldwide language support"

```
py -m pip install --upgrade pip
py -m pip install setuptools wheel py7zr==0.20.*
py -m pip install aqtinstall==3.1.*
py -m aqt version
py -m aqt install-qt windows desktop 5.15.2 win64_msvc2019_64 --autodesktop --outputdir C:\a\Capture2TextPlus/Qt

cd /d C:\a\Capture2TextPlus
git clone https://github.com/setsumi/Capture2TextPlus.git
cd Capture2TextPlus

pip install --force-reinstall -v "conan==1.64.1"
conan install . --build=missing
```
Build:
```
call "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\VC\Auxiliary\Build\vcvarsall.bat" x64
qmake
nmake
nmake clean
qmake CONFIG+=console
nmake
```
or use Qt Creator to build the project.
After build copy `lib/*.dll` to the same folder as Capture2Text.exe file.In the same Capture2Text.exe folder, create a folder called `tessdata` and put the trained data into it.

### Known issues:

* Compile with Visual Studio on Windows, should set runtime library to `/MD` but not `/MDd`
