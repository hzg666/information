# Mac安装nodejs环境
## 安装流程
### 1、github搜索nvm，进入项目(https://github.com/creationix/nvm)

### 2、安装nvm

```
➜  soft curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 11329  100 11329    0     0   6222      0  0:00:01  0:00:01 --:--:--  6224
=> Downloading nvm from git to '/Users/cony/.nvm'
=> Cloning into '/Users/cony/.nvm'...
remote: Counting objects: 6082, done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 6082 (delta 2), reused 0 (delta 0), pack-reused 6072
Receiving objects: 100% (6082/6082), 1.74 MiB | 54.00 KiB/s, done.
Resolving deltas: 100% (3752/3752), done.
* (HEAD detached at v0.33.0)
  master
=> Compressing and cleaning up git repository
Counting objects: 6082, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (6044/6044), done.
Writing objects: 100% (6082/6082), done.
Total 6082 (delta 4005), reused 1884 (delta 0)

=> Appending nvm source string to /Users/cony/.zshrc
=> bash_completion source string already in /Users/cony/.zshrc
=> Close and reopen your terminal to start using nvm or run the following to use it now:

export NVM_DIR="/Users/cony/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm

```

### 3、根据提示执行命令load nvm

```
➜  soft export NVM_DIR="/Users/cony/.nvm"
➜  soft [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
➜  soft nvm

Node Version Manager

Note: <version> refers to any version-like string nvm understands. This includes:
  - full or partial version numbers, starting with an optional "v" (0.10, v0.1.2, v1)
  - default (built-in) aliases: node, stable, unstable, iojs, system
  - custom aliases you define with `nvm alias foo`

 Any options that produce colorized output should respect the `--no-colors` option.

Usage:
  nvm --help                                Show this message
  nvm --version                             Print out the latest released version of nvm
  nvm install [-s] <version>                Download and install a <version>, [-s] from source. Uses .nvmrc if available
    --reinstall-packages-from=<version>     When installing, reinstall packages installed in <node|iojs|node version number>
    --lts                                   When installing, only select from LTS (long-term support) versions
    --lts=<LTS name>                        When installing, only select from versions for a specific LTS line
  nvm uninstall <version>                   Uninstall a version
  nvm uninstall --lts                       Uninstall using automatic LTS (long-term support) alias `lts/*`, if available.
  nvm uninstall --lts=<LTS name>            Uninstall using automatic alias for provided LTS line, if available.
  nvm use [--silent] <version>              Modify PATH to use <version>. Uses .nvmrc if available
    --lts                                   Uses automatic LTS (long-term support) alias `lts/*`, if available.
    --lts=<LTS name>                        Uses automatic alias for provided LTS line, if available.
  nvm exec [--silent] <version> [<command>] Run <command> on <version>. Uses .nvmrc if available
    --lts                                   Uses automatic LTS (long-term support) alias `lts/*`, if available.
    --lts=<LTS name>                        Uses automatic alias for provided LTS line, if available.
  nvm run [--silent] <version> [<args>]     Run `node` on <version> with <args> as arguments. Uses .nvmrc if available
    --lts                                   Uses automatic LTS (long-term support) alias `lts/*`, if available.
    --lts=<LTS name>                        Uses automatic alias for provided LTS line, if available.
  nvm current                               Display currently activated version
  nvm ls                                    List installed versions
  nvm ls <version>                          List versions matching a given <version>
  nvm ls-remote                             List remote versions available for install
    --lts                                   When listing, only show LTS (long-term support) versions
  nvm ls-remote <version>                   List remote versions available for install, matching a given <version>
    --lts                                   When listing, only show LTS (long-term support) versions
    --lts=<LTS name>                        When listing, only show versions for a specific LTS line
  nvm version <version>                     Resolve the given description to a single local version
  nvm version-remote <version>              Resolve the given description to a single remote version
    --lts                                   When listing, only select from LTS (long-term support) versions
    --lts=<LTS name>                        When listing, only select from versions for a specific LTS line
  nvm deactivate                            Undo effects of `nvm` on current shell
  nvm alias [<pattern>]                     Show all aliases beginning with <pattern>
  nvm alias <name> <version>                Set an alias named <name> pointing to <version>
  nvm unalias <name>                        Deletes the alias named <name>
  nvm reinstall-packages <version>          Reinstall global `npm` packages contained in <version> to current version
  nvm unload                                Unload `nvm` from shell
  nvm which [<version>]                     Display path to installed node version. Uses .nvmrc if available
  nvm cache dir                             Display path to the cache directory for nvm
  nvm cache clear                           Empty cache directory for nvm

Example:
  nvm install v0.10.32                  Install a specific version number
  nvm use 0.10                          Use the latest available 0.10.x release
  nvm run 0.10.32 app.js                Run app.js using node v0.10.32
  nvm exec 0.10.32 node app.js          Run `node app.js` with the PATH pointing to node v0.10.32
  nvm alias default 0.10.32             Set default node version on a shell

Note:
  to remove, delete, or uninstall nvm - just remove the `$NVM_DIR` folder (usually `~/.nvm`)
  
  ```
  
### 4、使用nvm安装node(根据自己需求安装相应版本)

```
➜  soft nvm install node
Downloading and installing node v7.5.0...
Local cache found: $NVM_DIR/.cache/bin/node-v7.5.0-darwin-x64/node-v7.5.0-darwin-x64.tar.gz
Computing checksum with shasum -a 256
Checksums do not match: '13918730a8a1d38e4b4f2434744cbb2ed044b79c4c064b5021e4af1b3045c674' found, '97b54cc473710585c7277c1786cd7085eae157f6dc8f77b71bc4de1cb3dacda7' expected.
Checksum check failed!
Removing the broken local cache...
Downloading https://nodejs.org/dist/v7.5.0/node-v7.5.0-darwin-x64.tar.gz...
######################################################################## 100.0%
Computing checksum with shasum -a 256
Checksums matched!
Now using node v7.5.0 (npm v4.1.2)
Creating default alias: default -> node (-> v7.5.0)
```

### 5、验证node及npm版本

```
➜  soft node -v
v7.5.0
➜  soft npm -v
4.1.2
```

## 参照URL
https://www.jianshu.com/p/a41f4923e2eb
