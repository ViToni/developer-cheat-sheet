# Maven cheat sheet

## Dependecies / Download / Offline mode

### Download all sources and JavaDocs for the dependencies

```{r, engine='bash', count_lines}
mvn dependency:sources dependency:resolve -Dclassifier=javadoc
```

### Download all dependencies before going offline

```{r, engine='bash', count_lines}
mvn dependency:go-offline
```

### Using maven in offline mode

```{r, engine='bash', count_lines}
mvn -o clean build install
```

## Skipping tasks

### Skipping compilation of tests

```{r, engine='bash', count_lines}
mvn install -Dmaven.test.skip=true
```

### Skipping execution of tests

```{r, engine='bash', count_lines}
mvn install -DskipTests=false
```
