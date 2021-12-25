# When you just have too many files use xargs

[2020-04-21]

When
```
rm *.temp
```
fails because the you just have too many files to delete, do this redirection into xargs:
```
ls | grep ".temp" > remove.us
xargs rm <<<$(cat remove.us)
```