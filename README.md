# Capture2TextPlus

Mod of Capture2Text, sync from: https://sourceforge.net/projects/capture2text/

## Changes
- option "Output->Save captured image" saves properly cut image including some padding
- [breaking] "Call Executable" option became inoperable since it's field is used for padding size, calculated as min snap box dimension / value (default=3.0)

## Dependencies
Tesseract, Qt 5 (cannot be version 4), Leptonica

## Build instructions

### Windows:

```
pip install --force-reinstall -v "conan==1.64.1"
conan install . --build=missing
```
Then use qtcreator to build the project, after build copy `lib/*.dll` to the same folder as Capture2Text.exe file.
In the same Capture2Text.exe folder, create a folder called `tessdata` and put the trained data into it.

### Known issues:
* Compile with Visual Studio on Windows, should set runtime library to /MD but not /MDd
