# GitTools

`$ ./extractor.sh <source> <destination>`

`$ ./extractor.sh source-forge.git extracted-src-dir`

- To break down the git commits using a separator.

```
$ separator="======================================="; for i in $(ls); do printf "\n\n$separator\n\033[4;1m$i\033[0m\n$(cat $i/commit-meta.txt)\n"; done; printf "\n\n$separator\n\n\n"
```

---
## References

- [GitTools](https://github.com/internetwache/GitTools)