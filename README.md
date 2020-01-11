# developer-cheat-sheet

Collection of small helpers found over time

## git

### Exporting a file from a repository and importing it into another while keeping its history

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

## Maven

### Download all dependencies before going offline

```{r, engine='bash', count_lines}
mvn dependency:go-offline
```

### Download all sources and JavaDocs for the dependencies

```{r, engine='bash', count_lines}
mvn dependency:sources dependency:resolve -Dclassifier=javadoc
```

### Using maven in offline mode

```{r, engine='bash', count_lines}
mvn -o clean build install
```

### Skipping compilation of tests

```{r, engine='bash', count_lines}
mvn install -Dmaven.test.skip=true
```

### Skipping execution of tests

```{r, engine='bash', count_lines}
mvn install -DskipTests=false
```

## Tasmota

[Tasmota](https://github.com/arendst/Tasmota) is great to "free" ESP8266-based smart plugs which have not so smart software.

### Connect UART interface

[Connecting UART](https://esphome.io/devices/sonoff_s20.html#step-2-connecting-uart)

### Use LED only to show powerstate

```{r, engine='bash', count_lines}
LedState 1
```

See: [LedState](https://tasmota.github.io/docs/#/Commands?id=ledstate)

### Do not show WiFi / MQTT state using LED

```{r, engine='bash', count_lines}
SetOption31 1
```

See: [SetOption31](https://tasmota.github.io/docs/#/Commands?id=setoption31)

### Activate mDNS service announcement

```{r, engine='bash', count_lines}
SetOption55 1
```

See: [SetOption55](https://tasmota.github.io/docs/#/Commands?id=setoption55)

### Select WiFi with strongest signal on restart

```{r, engine='bash', count_lines}
SetOption56 1
```

See: [SetOption56](https://tasmota.github.io/docs/#/Commands?id=setoption56)
