# git cheat sheet

## Exporting a file from a repository and importing it into another while keeping its history

https://github.com/CNG/dotfiles/blob/master/files/zsh/config/git/functions/git-import

```{r, engine='bash', count_lines}
# creates patches from $object (either file or dir) including history
cd some_repo
git format-patch --thread -o "$temp_dir" --root -- "$object"

# replay patches into other repo
cd other_repo
git am "$temp_dir"/*.patch || git am --abort
```

### Clone with submodules

```{r, engine='bash', count_lines}
git clone --recursive https://host/dir/repo.git
```

### Clone the submodule if it was initially forgotten

```{r, engine='bash', count_lines}
cd cloned-repo
git submodule update --init --recursive
```

### Show all your remotes

```{r, engine='bash', count_lines}
git remote -v
```

### Renaming a remote

```{r, engine='bash', count_lines}
git remote rename old_name new_name
```

### Set user name and email

#### Globally

```{r, engine='bash', count_lines}
git config --global user.name "John Doe"
git config --global user.email johndoe@example-github.com
```

#### For current repository

```{r, engine='bash', count_lines}
git config --local user.name "John Doe"
git config --local user.email johndoe@example-company.com
```

### Rewrite git access from SSH to HTTPS

Rewritting the remote URL is especially useful when using submodules since submodules usually keep their remote regardless how the parent got cloned (setting can also be done per repo).

```{r, engine='bash', count_lines}
# rewrite SSH
git config --global url.https://gitserver/.insteadOf ssh://git@gitserver/

# rewrite git protocol
git config --global url.https://gitserver/.insteadOf git@gitserver/
```

### Change author (name/email) of last commit

```{r, engine='bash', count_lines}
git commit --amend --author "name <author@email.com>"
```

### Rebase including initial commit

```{r, engine='bash', count_lines}
git rebase -i --root
```

### Rebase starting with specific commit

Rebase commits starting and including `COMMIT` on top of `branch`:

```{r, engine='bash', count_lines}
git rebase --onto branch SHA_OF_COMMIT^
```

The `^` attached to `SHA_OF_COMMIT` is crucial so that `COMMIT` is also included in the rebase.
