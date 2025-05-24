```
dir ---> Lists directory contents.

dir /A <attributes>	---> List directory contents with the specified attributes.

dir /A:H ---> List hidden files in the current directory.

dir /A:R ---> List read-only files in the current directory.

cd --->	Prints current working directory.

chdir --->	Prints current working directory. Alternate command.

cd <path> --->	Changes the directory.

chdir <path> --->	Changes the directory. Alternate command.

tree <path> ---> Graphically displays the directory structure from the specified path.

tree /F <path> --->	Graphically displays the directory structure from the specified path, including files within the directory

cls ---> Clears the terminal.

mkdir <directory name> --->	Creates a directory in the current working directory(or specified directory) with the specified name.

md <directory name>	---> Creates a directory in the current working directory(or specified directory) with the specified name. Alias of mkdir.

rmdir <directory name> --->	Removes a directory in the current working directory(or specified directory) with the specified name.

rd <directory name> ---> Removes a directory in the current working directory(or specified directory) with the specified name. Alias of rmdir

rmdir /S <directory name> --->	Recursively removes all directories and files in the specified directory.

move [source] [destination] ---> Move file(s) from the source folder to the destination folder.

copy [source] [destination]	---> Copy file(s) from the source folder to the destination folder. Only works with files and not folders.

copy [source] [destination] /V --->	Copy file(s) from the source folder to the destination folder. Validates that the file or files are copied correctly.

xcopy [source] [destination] ---> Copy file(s) and folder(s) from the source folder to the destination folder. Replaced by Robocopy and currently deprecated.

xcopy /E [source] [destination] ---> Copy file(s) and folder(s) from the source folder to the destination folder, including empty directories.

xcopy /K [source] [destination] ---> Copy file(s) and folder(s) from the source folder to the destination folder. Retains the current attributes of the copied files.

robocopy [source] [destination] ---> Copy files(s) and folder(s) from the source folder to the destination folder. It has a more robust feature set compared to xcopy.

robocopy /E /MIR /A-:SH [source] [destination] --->	Copy files(s) and folder(s) from the source folder to the destination folder. Mirrors the destination 
directory to the source and clears any additional attributes using the /A-:SH parameter.


more <file> ---> Displays the output of a file or command one screen at a time.

more /S <file> --->	Displays the output of a file or command one screen at a time. Compresses multiple blank lines into a single line.

<command> | more ---> Displays the output of a command through a <PIPE> to more.

type <file> ---> Displays the contents of a file.

fsutil file createNew <filename> <length> ---> Creates a new file with a specified file name and length.

echo "example string" > <filename> ---> Writes the contents provided into a new or existing file with the specified filename. If the file does not exist, a new one will be created; otherwise, the previous file's contents will be overwritten.

echo "example string" >> <filename> ---> Appends the provided contents to an existing file.

ren <filename1> <filename2> ---> Renames a file.

del <file> ---> Deletes a file or files.

del /A:R <file> ---> Deletes a file or files with the read-only attribute set.

del /A:H <file> ---> Deletes a file or files with the hidden attribute set.

erase <file> ---> Deletes a file or files. Interchangeable with del command.
```