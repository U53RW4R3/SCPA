# Manual

## Git

In the web browser by checking the git commits. You can identify emails and timezones from the specific repository.

```
https://github.com/<username>/<git_repo>/commit/<commit_id>

https://github.com/<username>/<git_repo>/commit/<commit_id>.patch
```

Clone the source repository.

```
$ git clone <URL>
```

Check the logs to search for emails other sensitive details such as, credentials.

```
$ git [--no-pager] log

$ git [--no-pager] log -p

$ git [--no-pager] log --stat
```

Enumerate the available branches of the source repository.

```
$ git branch -r
```

Switch to a different branch that you can view logs.

```
$ git checkout <branch>
```

Enumerate the available tags then display the contents.

```
$ git tag -l

$ git show <tag>
```

## SVN

Enumerate contents of the source repository.

```
$ svn ls svn://<IP>
```

Check the logs to search for emails other sensitive details such as, credentials.

```
$ svn log svn://<IP>
```

Clone the source repository.

```
$ svn checkout svn://<IP>
```

Select the revision while inside the directory from a cloned repository.

```
$ svn up -r <revision_ID>
```

Pull the changes by selecting a revision while inside the directory from a cloned repository.

```
$ svn update -r <revision_ID>
```

---
## References

### Backlinks

- [[DataSurgeon|DataSurgeon]]