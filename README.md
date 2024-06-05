# Capture2TextPlus

Mod of Capture2Text, sync from: https://sourceforge.net/projects/capture2text/

## Changes

- option "Output->Save captured image" saves properly cut image including some padding
- hot key cycle of text orientation goes between Horizontal and Vertical ignoring Auto
- updated to tesseract 5.3.3 from [here](https://conan.io/center/recipes?value=tesseract)

## Dependencies

Tesseract, Qt 5 (cannot be version 4), Leptonica

## Build instructions

### Windows:
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
Then use Qt Creator to build the project, after build copy `lib/*.dll` to the same folder as Capture2Text.exe file.
In the same Capture2Text.exe folder, create a folder called `tessdata` and put the trained data into it.

### Known issues:

* Compile with Visual Studio on Windows, should set runtime library to `/MD` but not `/MDd`
