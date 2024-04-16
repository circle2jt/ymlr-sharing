# github npm-up-version
Auto collect logs then commit before update a new version in typescript, nodejs project

## Run via CLI
```sh
  npx ymlr 
    -e PREID=${PREID} \
    -e VERSIONNAME=${VERSIONNAME} \
    -e COMMITFORMAT=${COMMITFORMAT} \
    -e CHANGEDIR=${CHANGEDIR} \
    -e CHANGEFILE=${CHANGEFILE} \
    -e COMMITFILES=${COMMITFILES} \
    -e FORCE=${FORCE} \
    -- \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/github/npm-up-version/index.yaml
```
Example: 
```sh
  npx ymlr \
    -e PREID=alpha \
    -e VERSIONNAME=prerelease \
    -e CHANGEDIR=~~/changes \
    -e CHANGEFILE=~~/CHANGES.md \
    -e COMMITFILES=~~/package.json,~~package-lock.json \
    -e FORCE=true \
    -- \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/github/npm-up-version/index.yaml
```

## Run in a docker
```sh
  docker run --rm -it --name auto-npm-up-version \
    -e PREID=${PREID} \
    -e VERSIONNAME=${VERSIONNAME} \
    -e COMMITFORMAT=${COMMITFORMAT} \
    -e CHANGEDIR=${CHANGEDIR} \
    -e CHANGEFILE=${CHANGEFILE} \
    -e COMMITFILES=${COMMITFILES} \
    -e FORCE=${FORCE} \
    circle2jt/ymlr \
    https://raw.githubusercontent.com/circle2jt/ymlr-sharing/main/github/npm-up-version/index.yaml
```
- `PREID`:            Identifier to be used to prefix premajor, preminor, prepatch or prerelease version increments. (`alpha`, `beta`, ... Default is empty)
- `VERSIONNAME`:      Version name to update. (`major`, `minor`, `patch`, `premajor`, `preminor`, `prepatch`, `prerelease`. Default is `prerelease`)
- `COMMITFORMAT`:     Format commit when update to next version. (Default `chore[^:]*: ${$vars.matchVersion}([^ ]+)`)
- `CHANGEDIR`:        Path of directory which includes the changing files for each of commit. (Default `./changes`)
- `CHANGEFILE`:       Changing logs will be saved to this path. (Default `./CHANGES.md`)
- `COMMITFILES`:      Path of files which are included to add into git commit
- `FORCE`:            auto pick the default values without asking (`true`, `false`)