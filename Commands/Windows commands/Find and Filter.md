```
where <file> ---> Displays the location of file(s) provided.

where /R <working directory> <file> ---> Recursively searches for the file(s) provided starting from the specified directory.

find "example string" <file> ---> Searches for a string of text in a file or files, and displays lines of text that contain the specified string.

findstr ---> Searches for patterns of text in files. Similar to grep on Unix/Linux.

comp <file1> <file2> ---> Compares the contents of two files or sets of files byte-by-byte.

fc <file1> <file2> ---> Compares two files or sets of files and displays the differences between them.

sort ---> Reads input, sorts data, and writes the results to the screen, a file, or another device.

Get-ChildItem -Path C:\Users\MTanaka\ -File -Recurse ---> List all File objects in the directory specified.

Get-Childitem -Path C:\Users\MTanaka\ -File -Recurse -ErrorAction SilentlyContinue <PIPE> where {($_.Name -like "*.txt")} ---> Search for all objects with the '.txt' file extension.

Get-Childitem –Path C:\Users\MTanaka\ -File -Recurse -ErrorAction SilentlyContinue <PIPE> where {($_.Name -like "*.txt" -or $_.Name -like "*.py" -or $_.Name -like "*.ps1" -or $_.Name -like "*.md" -or $_.Name -like "*.csv")} ---> Search for objects matching a list of different file extensions.

Get-ChildItem -Path C:\Users\MTanaka\ -Filter "*.txt" -Recurse -File <PIPE> sls "Password","credential","key" ---> Searching for keywords within an object's content.
```