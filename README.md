## Visual Studio Project Creator
This python script creates Visual Studio projects for you using template directories! 
This comes in handy if you don´t want to change all the settings every time you create a new project in Visual Studio or if you want all your projects to be structured the same way.

The created projects feature:
- Clean build environment
- Auto include the correct `.lib` files for the current build target
- Auto copy the correct `.dll`s to the bin directory
- The build executables do not need any Visual Studio Redistributable Packages to run on other machines

Generated folder structure:
- `bin` Here are several subdirectories generated after build that contain your final `exe`s
- `build` Internal Visual Studio stuff. *just ignore it ;)*
- `include` Here are your `.h` header files stored
- `lib` In the two subdirectories corresponding to the different build targets you can put your additional `.lib`s and `.dll`s. Note: The`.dll`s are automatically copied to the `bin` directory
  - `x64` 
  - `x86`
- `run` In this folder, the program is run by Visual Studio. Put files that the project uses while running there but no `.dll`s
- `src` Here comes your code

## Requirements
- python 2.7+ and python 3 (should work with all modern versions)

# Configuration
In the top of the `createproject.py` you can configure:
- `emptydirs_file_name = ".emptydirs"` This is necessary because you can´t push empty dirs in git. But if you use it on your local computer you can just create empty directories in your template folder! But don´t delete this file as it is used to identify template directories in input mode (not when specified by command-line)!

# Usage
## Windows
Run `createproject.bat` in the folder you want the project to be created or just double click it and move the folder afterwards.
You will be prompted with the project´s name and template.
## Linux
Run `createproject.sh` in the folder you want the project to be created.
You will be prompted with the project´s name and template.
## Other (using python)
Run `python createproject.py [-i] [TEMPLATE NAME] [PROJECT NAME]` in the folder you want the project to be created.
Invoking the `-i` option will prompt you with the project´s name and template.

# Custom templates
Of course this is a pretty simple script that can be applied to different templates. To use your own template (It could be for whatever you want) simply modify / replace the files in the `template` folder.
Use `$PROJECTNAME$` as a wildcard / dummy in filenames and file contents for the project´s name.
Use `$UUID_*NUMBER IDENTIFIER*$` as a wildcard for randomly generated UUID´s.
Note: The identifier only corresponds to one UUID (template wide, not just the file!) after first use.

`$UUID_123$` in file a == `$UUID_123$` in file b.

Have fun using this small but hopefully useful script.

Simon
