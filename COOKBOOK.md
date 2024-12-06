```
# diff filenames of 2 directories / -r recursive / -q quiet
diff -rq src1 src2

# merge directories
rsync -abviuzP --dry-run src/ dest/
```
