# git status不能正常显示中文文件名
```bash
git config --global core.quotepath false

```

或在($HOME/.gitconfig)中添加：
```
[core]
  quotepath = false

```

## 参考
* <http://stackoverflow.com/questions/4144417/how-to-handle-asian-characters-in-file-names-in-git-on-os-x>
